branch
=======

# 1. Demo

## 1.1. 创建并切换分支

```git
git checkout -b dev
```

相当于下面两行命令：

```git
git branch dev
git checkout dev
```

## 1.2. 查看当前所有分支

```git
git branch
```

会列出所有分支，当前分支前面标有 `*`

## 1.3. 在dev分支上工作

```git
git add readme.txt
git commit -m "readme.txt"
```

## 1.4. 切换回 master

```git
git checkout master
```

## 1.5. dev 合并到 master

```git
git merge dev
```

**注意**：默认合并为 **“快进模式”(Fast-forward)**

## 1.6. 删除 dev 分支

```git
git branch -d dev
git branch
```

# 2. 分支操作

## 2.1. 查看分支

```git
git branch
```

## 2.2. 创建分支

```git
git branch <name>
```

## 2.3. 切换分支

```git
git checkout <name>
```

**创建 + 切换**分支:

```git
git checkout -b <name>
```

## 2.4. 合并某分支到当前分支

```git
git merge <name>
```

## 2.5. 删除分支

```git
git branch -d <name>
```

# 3. 解决冲突

## 3.1. 冲突的发生

```git
<!-- 创建了一个名为 readme.txt 的文件 -->
touch readme.txt

<!-- 创建并切换到一个新的分支 feature1 -->
git checkout -b feature1

<!-- 在 readme.txt 文件中做修改 -->

<!-- 提交在 feature1 分支下对 readme.txt 文件的修改 -->
git add readme.txt
git commit -m "modification on branch feature1"

<!-- 切换到master分支 -->
git checkout master

<!-- 在 readme.txt 文件中做修改，注意：为了效果，这次修改要和在 feature1 分支下的修改内容不相同 -->

<!-- 提交在 master 分支下对 readme.txt 文件的修改 -->
git add readme.txt
git commit -m "modification on branch master"

<!-- 在 master 分支下企图合并 featur1 分支，但是产生冲突！ -->
git merge feature1

Auto-merging readme.txt
CONFLICT (content): Merge conflict in readme.txt
Automatic merge failed; fix conflicts and then commit the result.
```

**冲突** 的示意图：

![conflict](assets/conflict.png "conflict")

## 3.2. 冲突的查看

```git
<!-- 查看冲突的具体情况 -->
git status

<!-- 查看冲突文件 -->
cat readme.txt

readme.txt
<<<<<<< HEAD
modification on branch master
=======
modification on branch feature1
>>>>>>> feature1

<!-- 查看git日志 -->
git log --pretty=oneline
```

Git 用```<<<<<<<```，```=======```，```>>>>>>>``` 标记出不同分支的内容。

## 3.3. 冲突的解决

```git
<!-- 修改 readme.txt 文件内容 -->

<!-- 提交对冲突文件的修改 -->
git add readme.txt
git commit -m "conflict fixed"

<!-- 删除 feature1 分支 -->
git branch -d feature1
```

```git
<!-- 看分支的合并情况 -->
git log --graph --pretty=oneline --abbrev-commit

<!-- 看分支合并图 -->
git log --graph
```

**冲突解决** 的示意图：

![conflict2](assets/conflict2.png "conflict2")

# 4. 分支管理策略

# 5. Bug分支

# 6. Feature分支

# 7. 多人协作


参考
======

[廖雪峰的官方网站](https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000/001375840202368c74be33fbd884e71b570f2cc3c0d1dcf000)
