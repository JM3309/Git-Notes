branch
=======
<!-- TOC -->

- [1. Demo](#1-demo)
    - [1.1. 创建并切换分支](#11-创建并切换分支)
    - [1.2. 查看当前所有分支](#12-查看当前所有分支)
    - [1.3. 在dev分支上工作](#13-在dev分支上工作)
    - [1.4. 切换回 master](#14-切换回-master)
    - [1.5. dev 合并到 master](#15-dev-合并到-master)
    - [1.6. 删除 dev 分支](#16-删除-dev-分支)
- [2. 分支操作](#2-分支操作)
    - [2.1. 查看分支](#21-查看分支)
    - [2.2. 创建分支](#22-创建分支)
    - [2.3. 切换分支](#23-切换分支)
    - [2.4. 合并某分支到当前分支](#24-合并某分支到当前分支)
    - [2.5. 删除分支](#25-删除分支)
- [3. 解决冲突](#3-解决冲突)
    - [3.1. 冲突的发生](#31-冲突的发生)
    - [3.2. 冲突的查看](#32-冲突的查看)
    - [3.3. 冲突的解决](#33-冲突的解决)
- [4. 分支管理策略](#4-分支管理策略)
- [5. Bug分支](#5-bug分支)
- [6. Feature分支](#6-feature分支)
- [7. 多人协作](#7-多人协作)

<!-- /TOC -->
# 1. Demo

## 1.1. 创建并切换分支

```git
$ git checkout -b dev
```

相当于下面两行命令：

```git
$ git branch dev
$ git checkout dev
```

## 1.2. 查看当前所有分支

```git
$ git branch
```

会列出所有分支，当前分支前面标有 `*`

## 1.3. 在dev分支上工作

```git
$ git add readme.txt
$ git commit -m "readme.txt"
```

## 1.4. 切换回 master

```git
$ git checkout master
```

## 1.5. dev 合并到 master

```git
$ git merge dev
```

**注意**：默认合并为 **“快进模式”(Fast-forward)**

## 1.6. 删除 dev 分支

```git
$ git branch -d dev
$ git branch
```

# 2. 分支操作

## 2.1. 查看分支

```git
$ git branch
```

## 2.2. 创建分支

```git
$ git branch <name>
```

## 2.3. 切换分支

```git
$ git checkout <name>
```

**创建 + 切换**分支:

```git
$ git checkout -b <name>
```

## 2.4. 合并某分支到当前分支

```git
$ git merge <name>
```

## 2.5. 删除分支

```git
$ git branch -d <name>
```

# 3. 解决冲突

## 3.1. 冲突的发生

```git
<!-- 创建了一个名为 readme.txt 的文件 -->
$ touch readme.txt

<!-- 创建并切换到一个新的分支 feature1 -->
$ git checkout -b feature1

<!-- 在 readme.txt 文件中做修改 -->

<!-- 提交在 feature1 分支下对 readme.txt 文件的修改 -->
$ git add readme.txt
$ git commit -m "modification on branch feature1"

<!-- 切换到master分支 -->
$ git checkout master

<!-- 在 readme.txt 文件中做修改，注意：为了效果，这次修改要和在 feature1 分支下的修改内容不相同 -->

<!-- 提交在 master 分支下对 readme.txt 文件的修改 -->
$ git add readme.txt
$ git commit -m "modification on branch master"

<!-- 在 master 分支下企图合并 featur1 分支，但是产生冲突！ -->
$ git merge feature1

Auto-merging readme.txt
CONFLICT (content): Merge conflict in readme.txt
Automatic merge failed; fix conflicts and then commit the result.
```

**冲突** 的示意图：

![冲突发生示意图](assets/conflict.png)

## 3.2. 冲突的查看

```git
<!-- 查看冲突的具体情况 -->
$ git status

<!-- 查看冲突文件 -->
$ cat readme.txt

readme.txt
<<<<<<< HEAD
modification on branch master
=======
modification on branch feature1
>>>>>>> feature1

<!-- 查看git日志 -->
$ git log --pretty=oneline
```

Git 用```<<<<<<<```，```=======```，```>>>>>>>``` 标记出不同分支的内容。

## 3.3. 冲突的解决

```git
<!-- 修改 readme.txt 文件内容 -->

<!-- 提交对冲突文件的修改 -->
$ git add readme.txt
$ git commit -m "conflict fixed"

<!-- 删除 feature1 分支 -->
$ git branch -d feature1
```

```git
<!-- 看分支的合并情况 -->
$ git log --graph --pretty=oneline --abbrev-commit

<!-- 看分支合并图 -->
$ git log --graph
```

**冲突解决** 的示意图：

![冲突解决示意图](assets/conflict2.png)

# 4. 分支管理策略

合并分支时，如果可能，`Git`会用`Fast forward`模式，但这种模式下，删除分支后，会丢掉**分支信息**。如果要强制禁用`Fast forward`模式，`Git`就会在`merge`时生成一个新的`commit`，这样，从分支历史上就可以看出分支信息。

```git
<!-- 创建一个名为 hello.txt 的文件，做一些编辑并提交 -->
$ touch hello.txt
$ vi hello.txt
$ git add hello.txt
$ git commit -m "create hello.txt"

<!-- 创建 dev 分支，编辑 hello.txt 文件并提交 -->
$ git branch -b dev
$ vi hello.txt
$ git add hello.txt
$ git commit -m "mod on dev"

<!-- 切换到 master 分支 -->
$ git checkout master

<!-- 禁用 ff 模式合并 dev 分支 -->
$ git merge --no-ff -m "merge with no-ff" dev

<!-- 查看分支历史 -->
$ git log --graph --pretty=oneline --abbrev-commit
ev-commit 
*   5c0f2cf merge with no-ff
|\  
| * 1b0ea6d mod on dev
|/  
* 43f740e create hello.txt
```

在实际开发中，我们应该按照几个**基本原则**进行分支管理：

1. `master`分支应该是非常稳定的，也就是仅用来发布新版本，平时不能在上面干活
2. 干活都在`dev`分支上，也就是说，`dev`分支是不稳定的
3. 比如1.0版本发布时，再把`dev`分支合并到`master`上，在`master`分支发布1.0版本
4. 你和你的小伙伴们每个人都在`dev`分支上干活，每个人都有自己的分支，时不时地往`dev`分支上合并就可以了

![分支管理示意图](assets/branchs.png)

# 5. Bug分支

`Git` 允许你保存当前工作状态，创建一个 Bug 分支去修复 Bug，然后切换回来继续工作。

```git
<!-- 1. 在 dev 分支下保存工作现场 -->
$ git status
$ git stash
<!-- 现在查看工作区就是干净的 -->
$ git status

<!-- 2. 假设bug发生在 master 分支，创建一个 issue-101 分支用于修复Bug -->
$ git checkout master
$ git checkout -b issue-101

<!-- 3. 在 issue-101 分支下修复文件，假设只是修改了 readme.txt 文件 -->

<!-- 4. 提交修复代码 -->
$ git add readme.txt 
$ git commit -m "fix bug 101"

<!-- 5. 在 master 分支下 合并 issue-101 分支 -->
$ git checkout master
$ git merge --no-ff -m "merged bug fix 101" issue-101

<!-- 6. 返回 dev 分支继续工作 -->
$ git checkout dev
$ git status
$ git stash list
$ git stash pop
```

```git
<!-- 当只有一个工作现场时 -->
<!-- pop 命令恢复工作现场，并且在 stash list 中删除对应的记录 -->
$ git stash pop
<!-- 等价于 -->
<!-- 其中是 apply 命令恢复， 
    drop 命令删除 stash list 中的记录 -->
$ git stash apply
$ git stash drop

<!-- 当存在多个工作现场时 -->
<!-- 查看工作现场列表 -->
$ git stash list
<!-- 恢复指定的 stash -->
$ git stash apply stash@{0}
```

# 6. Feature分支

软件开发中，总有无穷无尽的新的功能要不断添加进来。添加一个新功能时，你肯定不希望因为一些实验性质的代码，把主分支搞乱了，所以，每添加一个新功能，最好新建一个 feature 分支，在上面开发，完成后，合并，最后，删除该 feature 分支。

```git
<!-- 1. 在 dev 分支下创建一个 feature-vulcan 的功能分支 -->
$ git checkout -b feature-vulcan

<!-- 2. 开发代码，假设就一个代码文件 vulcan.py 文件 -->
$ git add vulcan.py
$ git commit -m "add feature vulcan"

$ git checkout dev

<!-- 3. 如果功能顺利开发 -->
$ git merge --no-ff -m "merged feature vulcan" feature-vulcan

<!-- 3. 如果功能取消 -->
<!-- 执行正常删除分支的命令
    提示 feature-vulcan 分支没有被合并，删除分支会丢失修改 -->
$ git branch -d feature-vulcan
<!-- 需要强行删除 feature-vulcan 分支 -->
$ git branch -D feature-vulcan
```

# 7. 多人协作


参考
======

[廖雪峰的官方网站](https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000/001375840202368c74be33fbd884e71b570f2cc3c0d1dcf000)
