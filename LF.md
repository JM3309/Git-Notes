Git 多平台换行符问题(LF or CRLF)
======

文本文件所使用的换行符，在不同的系统平台上是不一样的。

* UNIX/Linux 使用的是 0x0A（LF）
* 早期的 Mac OS 使用的是 0x0D（CR），后来的 OS X 在更换内核后与 UNIX 保持一致了
* DOS/Windows 一直使用 0x0D0A（CRLF） 作为换行符

跨平台协作开发是常有的，不统一的换行符确实对跨平台的文件交换带来了麻烦。最大的问题是，在不同平台上，换行符发生改变时，Git 会认为整个文件被修改，这就造成我们没法 `diff` ，不能正确反映本次的修改。还好 Git 在设计时就考虑了这一点，其提供了一个 `autocrlf` 的配置项，用于在提交和检出时自动转换换行符，该配置有三个可选项：

* `true`: 提交时转换为 LF，检出时转换为 CRLF
* `false`: 提交检出均不转换
* `input`: 提交时转换为LF，检出时不转换

```git
# 提交时转换为LF，检出时转换为CRLF
$ git config --global core.autocrlf true

# 提交时转换为LF，检出时不转换
$ git config --global core.autocrlf input

# 提交检出均不转换
$ git config --global core.autocrlf false
```

如果把 `autocrlf` 设置为 `false` 时，那另一个配置项 `safecrlf` 最好设置为 ture 。该选项用于检查文件是否包含混合换行符，其有三个可选项：

* `true`: 拒绝提交包含混合换行符的文件
* `false`: 允许提交包含混合换行符的文件
* `warn`: 提交包含混合换行符的文件时给出警告

```git
# 拒绝提交包含混合换行符的文件
$ git config --global core.safecrlf true

# 允许提交包含混合换行符的文件
$ git config --global core.safecrlf false

# 提交包含混合换行符的文件时给出警告
$ git config --global core.safecrlf warn
```

手动将文件的换行符转化为 LF，这可以通过编辑器来完成，大部分编辑器都可以将文件的换行符风格设置为 unix 的形式。也可以使用 dos2unix 转换工具来完成，Windows 上 Git bash 客户端自带了该工具。其他系统上也可以安装该工具，例如 Ubuntu 上安装：

```shell
$ sudo apt-get install dos2unix
#  使用转换工具
$ find . -type f | xargs dos2unix
# or
$ find . -type f -exec dos2unix {} +
```

资料来源
======

[旷世的忧伤 的博客 -- Git 多平台换行符问题(LF or CRLF)](http://kuanghy.github.io/2017/03/19/git-lf-or-crlf)
