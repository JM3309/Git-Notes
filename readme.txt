Git is a distributed version control system.
Git is free software distributed under the GPL.

1 git安装后设置全局变量
$ git config --global user.name "Your Name"
$ git config --global user.email "email@example.com"

2 到目标目录下初始化一个Git仓库
$ git init

3 添加文件到Git仓库，分两步：
3.1 使用命令git add <file>，注意，可反复多次使用，添加多个文件；
$ git add perceptron.py
3.2 使用命令git commit -m <message>，完成。
$ git commit -m "perceptron.py"

4 查看工作区当前的状态
$ git status

5 查看被修改的内容
$ git diff readme.txt 

6 HEAD指向的版本就是当前版本
$ git reset --hard HEAD^

7 Git允许我们在版本的历史之间穿梭
$ git reset --hard commit_id

8 查看提交历史，以便确定要回退到哪个版本
$ git log
$ git log --pretty=oneline

9 查看命令历史，以便确定要回到未来的哪个版本
$ git reflog

10 丢弃工作区的修改
$ git checkout -- file
例如：
$ git checkout -- readme.txt
把readme.txt文件在工作区的修改全部撤销，这里有两种情况：
一种是readme.txt自修改后还没有被放到暂存区，
撤销修改就回到和版本库一模一样的状态；
一种是readme.txt已经添加到暂存区后，又作了修改,
撤销修改就回到添加到暂存区后的状态。

11 把暂存区的修改撤销掉（unstage），重新放回工作区
$ git reset HEAD <file>

12 删除文件
在工作区删除文件
$ rm test.txt
只是在工作区删除了文件，工作区和版本库不一致 
下有两个选择：
一是确实要从版本库中删除该文件
$ git rm test.txt
$ git commit -m "del test.txt"
另一种情况是删错了，把误删的文件恢复到最新版本
$ git checkout -- test.txt
git checkout其实是用版本库里的版本替换工作区的版本
无论工作区是修改还是删除，都可以“一键还原”

13 关联一个远程库，
$ git remote add origin git@server-name:path/repo-name.git

14 关联之后，第一次推送master分支的所有内容
$ git push -u origin master
此后，每次本地提交
$ git push origin master

15 克隆一个本地库
$ git clone git@github.com:fuerlai/git_learn.git
要克隆一个仓库，首先必须知道仓库的地址，然后使用git clone命令克隆。
Git支持多种协议，包括https，但通过ssh支持的原生git协议速度最快。
