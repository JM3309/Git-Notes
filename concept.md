 git 名词解释
 =======

# 1. 工作区(Working Dictinory)

* 项目的根目录
* 执行 `git init` 命令所在的目录
* `.git/` 文件夹所在的目录

# 2. 版本库(Repository)

1. 工作区有一个隐藏目录 `.git/`，这个不算工作区，而是**Git的版本库**
2. Git的版本库里存了很多东西
3. 其中最重要的就是称为`stage`（或者叫`index`）的暂存区
4. 还有Git为我们自动创建的第一个分支`master`
5. 以及指向`master`的一个指针叫`HEAD`
