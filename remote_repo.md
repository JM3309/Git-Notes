# remote_repo 

## 1. 创建SSH Key
#### 在用户主目录下，看看有没有.ssh目录
#### 如果有，再看看这个目录下有没有id_rsa和id_rsa.pub这两个文件，如果已经有了，可直接跳到下一步。
#### 如果没有：
#### $ ssh-keygen -t rsa -C "youremail@example.com"

## 2 登陆GitHub
#### 打开 Account settings > SSH Keys页面：
#### 点“Add SSH Key”，填上任意Title，在Key文本框里粘贴id_rsa.pub文件的内容：


# github

## 1. 新建仓库 
#### 登录GitHub，然后，在右上角找到Create a new repo按钮，创建一个新的仓库：

## 2. 在本地的learngit仓库下运行命令：
#### $ git remote add origin git@github.com:fuerlai/learngit.git
> 注意，把上面的fuerlai替换成你自己的GitHub账户名

## 3. 测试连接
#### $ ssh -T git@github.com

## 4. 上传到远程仓库
#### $ git push -u origin master(首次)
#### $ git push origin master

### Q1: 关于README.md文件
如果在GitHub上创建的repo勾选了README.md
但是本地版本库中没有README.md
push过程会报错：
##### ! [rejected]        master -> master (fetch first)
##### error: failed to push some refs to 'git@github.com:fuerlai/git_learn.git'
### Q1: 解决办法：
通过如下命令进行代码合并
#### $ git pull --rebase origin master
> 注：pull=fetch+merge

执行上面代码后可以看到本地代码库中多了README.md文件，然后再执行上传
> 或者先clone再push

### Q2: 下行命令之后报错
##### $ git remote add origin git@github.com:fuerlai/learn_dl_python3.git
##### bash: $'\302\203git': command not found
### Q2: 解决办法：
##### $ git status 
##### $ git remote add origin git@github.com:fuerlai/learn_dl_python3.git
##### $ ssh -T git@github.com
