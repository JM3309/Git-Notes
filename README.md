# git_learn

> Git is a distributed [version control](https://en.wikipedia.org/wiki/Version_control) system.
>
> Git is free software distributed under the [GPL](https://baike.baidu.com/item/GPL/2357903).

## 1. git安装后设置全局变量

```git
git config --global user.name "Your Name"
git config --global user.email "email@example.com"
```

## 2. 初始化一个Git仓库

**注意：** 在工作目录下执行下行命令

```git
git init
```

## 3. 添加文件到Git仓库

### 3.1 添加至暂存库

```git
git add mytext.txt
```

**注意：** 可反复多次使用，添加多个文件；

### 3.2 从暂存库添加至版本库

```git
git commit -m "mytext.txt"
```

## 4. 查看工作区当前状态

```git
git status
```

## 5. 查看被修改的内容

```git
git diff mytext.txt
```

## 6. HEAD指针

HEAD指向的版本就是当前版本

```git
git reset --hard HEAD^
```

## 7. 回到历史版本

```git
git reset --hard commit_id
```

## 8. 查看提交历史

```git
git log
```

或者只输出简略信息

```git
git log --pretty=oneline
```

## 9. 查看命令历史

```git
git reflog
```

**7、8、9的使用方法**：通过```git log```命令查看历史版本后，可以选择其中一个历史版本的```commit_id```，使用```git reset --hard commit_id```命令回到历史版本，回到历史版本后，使用```git reflog```命令获得命令版本，可以使用```git reset --hard commit_id```命令再次回到较新的版本。

## 10. 丢弃工作区的修改

```git
git checkout -- file
```

例如：

```git
git checkout -- readme.txt
```

**把readme.txt文件在工作区的修改全部撤销，这里有两种情况**:

一种是readme.txt自修改后还 **没有被放到暂存区**，
撤销修改就 **回到和版本库一模一样的状态**；

一种是readme.txt **已经添加到暂存区后**，又作了修改,
撤销修改就 **回到添加到暂存区后的状态**。

## 11. 撤销暂存区的修改

```git
git reset HEAD <file>
```

## 12. 删除文件

### 12.1 在工作区删除文件

```git
rm test.txt
```

### 12.2 只是在工作区删除了文件，工作区和版本库不一致

**下有两个选择**：

**情况一**：确实要从版本库中删除该文件

```git
git rm test.txt
git commit -m "del test.txt"
```

**情况二**：把误删的文件恢复到最新版本

```git
git checkout -- test.txt
```

* ```git checkout```其实是 **用版本库里的版本替换工作区的版本**
* 无论工作区是修改还是删除，都可以 **一键还原**

## 13. 关联远程库

```git
git remote add origin git@server-name:path/repo-name.git
```

例如关联 [GitHub](https://github.com/) :

```git
git remote add origin git@github.com:fuerlai/git_learn.git
```

## 14. 提交代码

第一次推送master分支的所有内容

```git
git push -u origin master
```

此后，每次本地提交使用命令

```git
git push origin master
```

## 15. 克隆一个本地库

```git
git clone git@github.com:fuerlai/git_learn.git
```

* 要克隆一个仓库，首先必须知道仓库的地址，然后使用git clone命令克隆。
* Git支持多种协议，包括 [**https** 协议](https://en.wikipedia.org/wiki/HTTPS) ，但通过 [**ssh**](https://zh.wikipedia.org/wiki/Secure_Shell) 支持的原生 [**git** 协议](https://git-scm.com/book/zh/v1/%E6%9C%8D%E5%8A%A1%E5%99%A8%E4%B8%8A%E7%9A%84-Git-%E5%8D%8F%E8%AE%AE) 速度最快。

> **资料来源**：[廖雪峰的官方网站](https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000)