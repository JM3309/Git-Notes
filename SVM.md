SVN 使用
======

# 1. 版本控制和版本控制工具

* CVS  <-- RCS
* SVN
* GIT

# 2. SVN 服务端和客户端的安装

* VisualSVN Server
* TortoiseSVN

# 3. 基本功能

1. 服务端新建仓库
2. 客户端同步仓库
3. 客户端提交代码 -- 增、删、改

# 4. Windows环境下使用客户端多人协作

1. update
2. commit
3. show log
4. revert -- A 提交版本冲突，且 B 正确，A 需要 revert
5. diff -- A 将自己的代码重命名，然后和 update 版本做对比
6. ...

# 5. 环境搭建

## 5.1. 服务端命令

```shell
# 控制 svm 系统服务的启动
$ svnserve
# 版本库的创建/导出/导入/删除
$ svnadmin
# 查看版本库的信息
$ svnlook
```

### 5.1.1. 创建版本库

```shell
$ svnadmin create /path/repos
```

```shell
$ svnadmin create --fs-type fsfs /path/repos
```

1. fsfs
2. dbd

### 5.1.2. 删除版本库

```shell
$ rm -rvf /path/repos
```

### 5.1.3. 版本库配置及权限分配

配置文件位于 `/path/repos/conf/`

修改配置一定要在版本库运行之前

1. authz -- 配置用户组以及用户组权限
2. passwd -- 配置用户名和密码
3. svnserve.conf -- 配置默认权限、权限配置文件及密码配置文件

```mermaid
graph TB;
    SVN服务器 == update ==> SVN客户端;
    SVN客户端 == commit ==> SVN服务器;
```b

```conf
# svnserve.conf
# 这个文件中的内容是注释掉的，需要自己解注
anon-access = read
auth-access = write
password-db = passwd
authz-db = authz
```

```conf
# passwd
zhangsan = 123456
```

```conf
# authz
[group]
pm = zhangsan
dev = hello,world
rookie = lisi

[/]
@pm = rw
@dev = r
@rookie = r

[repos: /xxx]
@pm = rw
hello = rw
world = r
lisi = 
```

### 5.1.4. 版本库的访问

服务器端启动版本库服务

```shell
svnserve -d -r /path/repos/
```

客户端检出工作副本

```shell
$ svn checkout svn://129.168.1.130 --username zhansgan --passwrod 123456
# or
$ svn co svn://129.168.1.130 --username zhansgan --passwrod 123456
```

### 5.1.5. SVN 服务自启动

`/etc/rc.local`

## 5.2. 客户端命令

```shell
# 版本库的检出/更新/提交/重定向
$ svn
```

# 6. 基本操作

## 6.1. SVN 术语

* 版本库
* 检出
* 工作副本
* 更新
* 提交
* 版本
* 版本号
* ...

## 6.2. 文件状态

* 无版本控制
* 增加
* 修改
* 常规
* 冲突
* 删除
* 锁定
* ...

## 6.3. checkout 和 export

1. checkout 检出的工作副本目录中含有 .svn 文件夹
2. 版本控制中有一种文件状态为无版本控制

```shell
$ svn checkout -r 2
$ svn export -r 3
```

## 6.4. add / commit / update / delete

* commit = ci
* checkout = co
* update = up
* delete = del = remove = rm

```shell
# 添加到版本控制
$ svn add
$ svn add js --non-recursive
$ svn add *
$ svn add * --force

# 提交修改到服务端
$ svn commit
# 备注强制要求
svn ci -m "hello" index.html

# 更新工作副本
$ svn update
$ svn up
$ svn up -r 2 index.html
$ svn up *

# 从版本库中删除文件或者目录
$ svn delete
# 备注非强制要求
svn rm index.html -m "xxxx"
svn ci -m ""
```

## 6.5. diff / mkdir / cat

* diff = di
* mkdir
* cat

```shell
# 版本差异比较
$ svn diff 
# 比较本地工作副本和服务器最后一次提交的版本之间的差异
$ svn di index.html
# 比较工作副本与任意历史版本之间的差异
$ svn di -r 2 index.html
# 比较任意两个历史版本之间的差异
$ svn di -r 1:3 index.html
# 批量比较差异，当前工作目录下所有文件，如果修改较多，输出很多，不推荐
$ svn di

# 创建目录并增加到版本控制
$ svn mkdir
$ svn mkdir doc

# 不检出工作副本直接查看指定文件
$ svn cat
$ svn cat svn://129.168.1.130/path/repos/index.html
```

## 6.6. revert

工作副本还原

```shell
$ svn revert [--recursive] [filename|*]
$ svn revert index.html
$ svn revert *
$ svn revert --recursive *
```

## 6.7. 二进制冲突和树冲突

1. 什么是冲突以及冲突产生的条件
2. 如何尽可能地避免冲突图
3. 如何解决冲突

### 6.7.1. 冲突及产生条件

* 冲突常出现于工作副本长时间未更新时
* 工作副本地修改正好与更新到的数据在同一处
* **经常更新工作副本可以尽量避免产生冲突**

### 6.7.2. 树冲突

* 发生树冲突的文件都**不是**二进制文本文件
* 树冲突无法精确到行并且处理树冲突，必须处理整个文件

### 6.7.3. 冲突处理

```shell
$ svn resolve index.html
$ svn resolved index.html
```

* p -- 
* df -- 
* e -- 
* m -- 
* mc -- 
* tc -- 
* s -- 

## 6.8. 锁定与解锁

```shell
# 锁定文件，防止其他成员对文件进行提交
$ svn lock index.html
# 默认锁定之后如果有提交操作，文件会自动解锁
# 如果提交之后还不想解锁文件
$ svn ci -m "" --no-unlock index.html

# 解锁文件
$ svn unlock index.html
```

# 7. 进阶应用

## 7.1. ls / st / log / info

```shell
# 列出当前工作目录下处于版本控制的所有文件
$ svn list
$ svn ls
$ svn ls --recursive
$ ls -l
$ ll
$ svn ls -v

# 列出工作副本文件（夹）的状态
$ svn status
$ svn st

# 查看提交日志（来自 svn ci 的 -m 参数）
$ svn log
$ svn log index.html

# 工作副本及文件（夹）的详细信息
$ svn info
$ svn info index.html
$ svn info --xml
# 使用管道保存版本库信息
$ svn info --xml >> info.xml
```

* ? -- 无版本控制
* D -- 
* M -- 
* A -- 
* R -- 删除某个文件之后又新建了一个同名文件
* C -- 存在冲突
* ! -- 文件缺失

## 7.2. 多版本库解决方案A

TCP/IP 协议规定端口号范围为 0 ~ 65535

* 公认端口 -- 0 ~ 1023
* 注册端口 -- 1024 ~  49151
* 私有端口 -- 49152 ~ 65535

举例

* 80
* 3306
* 3690

多个版本库，自己指定端口号

```shell
svnserve -d -r /path/hello/ --listen-port 3691
svnserve -d -r /path/world/ --listen-port 3692
```

修改配置一定要在版本库运行之前，如果已经开始运行后想要修改版本库，需要暂停SVN服务，配置，重启分配端口号。

```shell
$ killall svnserve
```

```shell
$ svn co svn://19.168.1.130:3691 hello3691
$ svn co svn://19.168.1.130:3692 world3692
```

## 7.3. 多版本库解决方案B

只使用一个端口号运行多个版本库，多个版本库放在同一个目录下

```shell
# 一次运行 svnroot 目录下所有的版本库
$ svnserve -d -r /svnroot/ 
```

```shell
$ svn co svn://19.168.1.130/hello
$ svn co svn://19.168.1.130/world
```

## 7.4. copy

1. 工作副本 --> 工作副本
2. 工作副本 --> 版本库
3. 版本库 --> 工作副本
4. 版本库 --> 版本库

```shell
$ svn copy
# 工作副本到工作副本
$ svn cp index.html copy.html
$ svn cp -r 4 index.html copyv4.html
$ svn mkdir temp
$ svn cp index.html about.html temp/

# 工作副本到版本库
# -m 参数必须加上
# 不支持跨库操作，提交是不能跨库的！
$ svn cp index.html svn://192.168.1.130/hello/target.html -m "copy index"

# 从版本库到工作副本
# 支持跨库操作
$ svn cp svn://192.168.1.130/hello/index.html demo.html
$ svn cp svn://192.168.1.130/world/index.html demo2.html

# 从版本库到版本库
# 不能跨库
# 主干版本与分hi版本小节中讲解
```

## 7.5. 主干版本与分支版本


```shell
# 创建主干版本
$ svn cp svn://192.168.1.130/hello svn://192.168.1.130/hello/trunk -m "setup a trunk"
# 创建分支版本
$ svn cp svn://192.168.1.130/hello/trunk svn://192.168.1.130/hello/branch -m "setup a branch"
```

一个版本库创建后，先创建两个文件夹

* trunk -- 主干版本
* branch -- 分支版本
* tag -- 已发布版本

# 高级应用

SVN 服务器级别的应用，使用这些应用 SVN 服务需要重启，影响使用用户

## hooks 钩子应用

何为钩子？当执行某些特定操作时触发预先设定好的任务。

```shell
$ cd hooks
$ ll
# *.tmpl
# 实际上就是 shell 脚本
$ cp -a post-commit.tmpl post-commit
$ chmod +x post-commit
$ vim post-commit
```

```bash
svn info svn://192.168.1.130/hello --xml >> /var/www/repo.xml
:wq
```

```shell
$ killall svnserve
$ svnserve -d -r /svnroot/
```

把 SVN 构建在 GIT 之上，利用钩子实现的！

## 版本库精简与丢弃

```shell
$ killall svnserve
$ svnadmin dump /svnroot/hello/ -r 6:16 > ~/hello.repo
$ svnadmin create /svnroot/newhello
$ svnadmin load /svnroot/newhello < ~/hello.repo
$ cp -av /svnroot/hello/conf/* /svnroot/newhello/conf/
$ rm -rvf /svnroot/hello
$ svnserve -d -r /svnroot/
```

做出版本库的精简后，之前的工作副本就不能提交了，需要重新检出工作副本

## 版本库的迁移和switch重定向

迁移一般发生在服务器更换时，迁移实际上与精简是一样的。

迁移的另一种方法，比较粗暴

1. killall svnserve
2. 把 /svnroot/repo/ 压缩为 repo.zip
3. 复制 repo.zip 到新服务器并解压
4. 在新服务器上运行 repo 版本库

重定向

```shell
$ killall svnserve
$ mv world newworld
$ svnserve -d -r /svnroot/
```

```shell
$ cd ~/world
$ svn switch
$ svn sw --relocate svn://192.168.1.130/world svn://192.168.1.130/newworld
```

