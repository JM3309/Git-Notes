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

