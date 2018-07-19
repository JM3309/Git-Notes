# markdown

## Markdown 使用场景

* 学习笔记
* 演讲稿
* 写书（侧重于技术相关的 内容非常适合）
* 个人笔记
* 文章博客
* 教学讲义
* 说明文档
* 电子邮件
* 只要有写作的地方，都可以使用 Markdown 来书写。

## Markdown安装与环境配置
* sublime
> 按下键 Ctrl+Shift+p 调出命令面板，找到 Package Control: install Pakage 这一项。搜索 markdown preview ，点击安装。
> Markdown Preview 较常用的功能是 preview in browser 和 Export HTML in Sublime Text ，前者可以在浏览器看到预览效果，后者可将 markdown 保存为 html 文件。
> preview in browser 据称是实时的，但是实践上还是需要在 st 保存，然后浏览器刷新才能看到新的效果，好在 markdown 写得多的话也不需要每敲一行看一次效果。
* webstorn
> 打开webstorm ，File-->Setting-->输入plugin-->Install JetBrains plugin...-->输入markdown-->点击右边的 Install ,安装完，重启 webstorm。
* vscode
> Visual Studio Code 自带 markdown 预览,所以不需要安装插件,不过可以安装语法高亮主题

### subline text
* MarkdownEditing 主题、自动补齐等功能
* MarkdownPreview 在浏览器预览
* MarkdownTOC 自动生成导航
* Table Editor 自动表格编辑
* packagecontrol Sublime 的插件生态系统网站


% 标题

# h1
## h2
### h3
#### h4 
##### h5
###### h6

h1
======
h2
------

% 水平线

* * *
***
*****
- - -
---------------------------------------

% 字体

1. **Bold**
2. __emphasize__
3. regular
4. *italic1*
5. _italic2_
6. _**组合强调**_
7. ~~delete~~
8. <del>del</del>

% 列表

* java
* python
* R
* javascript
* c#

+ item1
+ item2
+ item3

- item1
- item2
- item3

% 段落就是加空行

paragraph1

paragraph2

paragraph3

% 链接

[内嵌式链接](https://www.google.com)

[带标题的内嵌式链接](https://www.google.com "谷歌的主页")

[引用式链接][arbitrary case-insensitive reference text]

[相对引用一个库文件](README.md)

[你可以在引用式链接定义中使用数字][1]

或者空着什么都不写 [link text itself]

[arbitrary case-insensitive reference text]: https://www.mozilla.org
[1]: http://slashdot.org
[link text itself]: http://www.reddit.com

% 脚注

这是一段文字[^1]

这又是一段文字[^n]

[^1]: This is my first footnote
[^n]: Visit http://ghost.org
[^n]: A final footnote

% 图片

![内嵌式](pic1.png "图片的文字")
![引用式][pic]

[pic]: pic1.png "图片的文字"

% 代码

```javascript
var s = "JavaScript语法高亮";
alert(s);
```

```python
s = "Python语法高亮"
print s
```

```
没有指明语言，所有没有语法高亮。
让我们随便写个标签试试 <b>tag</b>
```

% 表格

| Tables        | Are           | Cool  |
| ------------- |:-------------:| -----:|
| col 3 is      | right-aligned | $1600 |
| col 2 is      | centered      |   $12 |
| zebra stripes | are neat      |    $1 |

Markdown | Less | Pretty
--- | --- | ---
*Still* | `renders` | **nicely**
1 | 2 | 3

% 引用

> 在邮件中块引用中很方便用来仿真文本的回复。
> 这行是同一个块的一部分。

引用结束

> 当这行很长的文字被包裹的时候，它依然会被恰当的引用。让我们继续写下去来确保包裹它时对于每个人来说它足够长。你可以*在*块引用中使用其它**Markdown**。

% 内嵌HTML(没有demo)

% 视频

[![IMAGE ALT TEXT HERE](http://i2.hdslb.com/bfs/archive/85dc88834df3825b6bf5a318386500c1bbb50504.jpg@160w_100h.jpg)](https://www.bilibili.com/video/av26945253/?spm_id_from=333.334.chief_recommend.16)

来源：

[GitBook](https://legacy.gitbook.com/book/chrisniael/gitbook-documentation/details)

[markdown官方文档](https://markdown-zh.readthedocs.io/en/latest/)
