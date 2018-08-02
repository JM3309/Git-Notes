# branch

## 1. demo

### 1.1 创建并切换分支

```git
git checkout -b dev
```

相当于下面两行命令：

```git
git branch dev
git checkout dev
```

### 1.2 查看当前所有分支

```git
git branch
```

会列出所有分支，当前分支前面标有```*```

### 1.3 在dev分支上工作

```git
git add readme.txt
git commit -m "readme.txt"
```

### 1.4 切换回 master

```git
git checkout master
```

### 1.5 dev 合并到 master

```git
git merge dev
```

**注意**：默认合并为 **“快进模式”(Fast-forward)**

### 1.6 删除 dev 分支

```git
git branch -d dev

git branch
```

## 2. 分支操作常用命令

### 2.1 查看分支

```git
git branch
```

### 2.2 创建分支

```git
git branch <name>
```

### 2.3 切换分支

```git
git checkout <name>
```

### 2.4 创建 + 切换分支

```git
git checkout -b <name>
```

### 2.5 合并某分支到当前分支

```git
git merge <name>
```

### 2.6 删除分支

```git
git branch -d <name>
```

## 3. 解决冲突

### 3.1 冲突的发生

```git
touch readme.txt

<!-- 创建并切换到一个新的分支 -->
git checkout -b feature1

<!-- 在readme.txt文件中做修改 -->

git add readme.txt
git commit -m "modification on branch feature1"

<!-- 切换到master分支 -->
git checkout master

<!-- 在readme.txt文件中做修改 -->

git add readme.txt
git commit -m "modification on branch master"

<!-- 企图合并分支，但是产生冲突 -->
git merge feature1

Auto-merging readme.txt
CONFLICT (content): Merge conflict in readme.txt
Automatic merge failed; fix conflicts and then commit the result.
```

冲突的示意图：

![conflict](conflict.png "conflict")

### 3.2 冲突的查看

```git
<!-- 查看冲突的具体情况 -->
git status

<!-- 查看冲突文件 -->
cat readme.txt
<!-- out -->
readme.txt
<<<<<<< HEAD
modification on branch master
=======
modification on branch feature1
>>>>>>> feature1

<!-- 查看git日志 -->
git log --pretty=oneline
<!-- out -->
15d79514f6eebf19bacb7a125e87eb65e275df99 (HEAD -> master) readme.txt
8b48325faaa81032b4fb165a1263b99a268cec28 <U+0096>conflict.png
ef73e9978adcdd6bbddd409297890a3df141349d <U+0096>modification on master
77d67999c9e9c36e57f777906fc12593426ae38d (feature1) <U+0096>modification on feature1
34657277ce95aef9ced515fe53e48c7a2ed6ea50 <U+0096>modification on feature1
```

Git 用```<<<<<<<```，```=======```，```>>>>>>>``` 标记出不同分支的内容

### 3.3 冲突的解决

```git
<!-- 修改readme.txt文件内容 -->

git add readme.txt
git commit -m "conflict fixed"

<!-- 删除feature1分支 -->
git branch -d feature1
```

```git
<!-- 看分支的合并情况 -->
git log --graph --pretty=oneline --abbrev-commit

<!-- 看分支合并图 -->
git log --graph
```

