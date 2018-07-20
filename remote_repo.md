# 远程仓库

## 1. 创建SSH Key

在用户主目录下，看看有没有 ```.ssh``` 目录

如果有，再看看这个目录下有没有 ```id_rsa``` 和```id_rsa.pub``` 这两个文件。

如果已经有了，可直接跳到下一步。

如果没有：

```ssh
ssh-keygen -t rsa -C "youremail@example.com"
```

## 2. 登录GitHub

打开 Account settings > SSH Keys 页面

点 “Add SSH Key”，填上任意 Title，在 Key 文本框里粘贴 id_rsa.pub 文件的内容

## 3. 新建仓库

登录GitHub，然后，在右上角找到 Create a new repo 按钮，创建一个新的仓库

## 4. 在本地仓库下运行命令

```git
git remote add origin git@github.com:fuerlai/learngit.git
```

**注意** ：把上面的 fuerlai 替换成你自己的 GitHub 账户名

## 5. 测试连接

```git
ssh -T git@github.com
```

## 6. 上传到远程仓库

```git
git push -u origin master(首次)
git push origin master
```

## Q1: 关于README.md文件

如果在 GitHub 上创建的 repo 勾选了 ```README.md``` ，
但是本地版本库中没有 ```README.md``` ，
push 过程会报错：

```git
#! [rejected]        master -> master (fetch first)
#error: failed to push some refs to 'git@github.com:fuerlai/git_learn.git'
```

## A1

通过如下命令进行代码合并

```git
git pull --rebase origin master
```

注：pull = fetch + merge

执行上面代码后可以看到本地代码库中多了 ```README.md``` 文件，然后再执行上传

**另一个解决办法**：先 clone 再 push

## Q2: 下行命令之后报错

```git
git remote add origin git@github.com:fuerlai/learn_dl_python3.git
#bash: $'\302\203git': command not found
```

## A2

```git
git status
git remote add origin git@github.com:fuerlai/learn_dl_python3.git
ssh -T git@github.com
git remote add origin
```
