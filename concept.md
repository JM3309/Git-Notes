 git名词解释
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

# 3. 仓库

![本地仓库和远程仓库](assets/git.jpeg)

假设项目代码存储在图中每台电脑中，图中服务器中的代码库就是项目**远程仓库**，而每台电脑中的代码库就是项目的**本地仓库**。

本地仓库和远程仓库的概念不是git独有的，在其他的版本控制工具（如：SVN、CVS）中也有相同的概念。

git真正强大之处在于**分布式**。

![git分布式](assets/git2.jpeg)

参考
====

[廖雪峰的官方网站](https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000)
