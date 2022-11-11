# Linux系统

## 一、简介

### 1. 操作系统

~~~markdown
调配硬件和软件资源，是直接运行在裸机上的最基本的系统软件，任何其他软件都必须在操作系统的支持下才能运行。
管理与配置内存、决定系统资源供需的优先次序、控制输入与输出设备、操作网络与管理文件系统
~~~

### 2. Linux系统

~~~markdown
Linux是一套免费使用和自由传播的一个类Unix系统。多任务、支持多线程、支持多CPU的操作系统。
操作系统两大阵营：
	1. windows：windows xp;7;vista;8;10;11
	2. Unix衍生系统：MAC OS（catelina/bigsure）；CentOS；redhat；ubuntu；红旗
Linux系统具有以下主要特性：
	1. 开放性：系统遵循了世界的标准规范
	2. 多用户：系统资源可以被不同用户各自拥有使用，每个用户都可以对自己的资源进行管理并且设置权限。
	3. 多任务：同时执行多个程序，并且每个程序之间的运行互相独立。Linux可以调度每一个进程，平等的访问微处理器。
	4. 良好的界面：同时具有字符界面和图形界面。
	5. 丰富的网络功能：内置了很多网络服务器软件、数据库和网页开发的工具。
	6. 可靠的系统安全：Linux采取了许多安全技术措施，包括对读、写控制、带保护的子系统、审计跟踪、核心授权等。
	7. 免费
	
总结：免费、安全、可靠、稳定、多平台
~~~

- 双系统（Linux和windows系统同时存在，开机的时候可以选择操作系统）
- 虚拟机

### 3. Linux的目录结构

- bin：存放二进制可执行文件
- sbin：存放二进制可执行文件，只有root才可以访问
- etc：存放系统配置文件
- usr：用于存放多用户共享的系统资源
- home：存放用户文件的根目录
- root：超级用户目录
- dev：用于存放设备文件
- lib：存放跟文件系统中的程序运行所需要的共享库以及内核模块
- tmp：用于存放临时文件

### 4. Linux的Shell

shell是系统的用户界面，提供了用户和内核进行交互操作的一种接口。它接收到用户输入的命令并且将命令送入内核中执行。

- Bourne Shell：贝尔实验室开发
- BASH：操作系统上默认的shell
- Korn Shell：对贝尔实验室的shell进行的改进
- C Shell：是SUN公司shell的一个版本

## 二、 基本命令

### 1、 简单的几个命令

- ls：显示指定目录下的文件的目录清单(list)
- cd：切换目录，改变当前的工作目录(change directory)
  - cd ~  切换到用户的主目录(家目录)
  - cd /   切换到根目录
  - cd ..  上一级目录
  - cd.    当前目录
- pwd：显示当前的工作目录
- man：查看帮助



### 2、 文件操作的基本命令

#### 2.1 ls命令

作用：显示制定目录下的文件清单

- 不带参数：显示当前目录下的内容
  - [root@10 /]# ls		显示当前目录下的内容
  - [root@10 /]# ls etc    显示etc目录下的内容
- ls -a：显示所有文件 包含隐藏文件(以.开头的文件)
- ls -l：显示文件的详细信息
- ls -R：递归的显示目录下的文件包括子文件
- ls -lR

#### 2.2 mkdir/rmdir命令

作用：创建目录/删除目录

- mkdir 创建目录
  - mkdir homework：创建一个homework目录
  - mkdir -p homeworks/duansenhao/jichenguang：连续创建多级目录
  - mkdir d{1..9}  同时创建d1,d2,....d9目录(了解)
- rmdir  删除目录(只能删除空目录)   

补充：创建文件 touch 文件名----touch 1.txt

#### 2.3 rm命令

作用：删除文件或目录

- rm 文件名：删之前会询问，要求确认
- rm -i：提示是否删除，默认是由提示的
- rm -f 文件名：强制删除
- rm -r 目录名：删除目录
  - rm -rf目录名：强制删除目录，没有提示

#### 2.4 cp命令

作用：拷贝文件或者目录

- cp 原文件名 新文件名
- cp 1.txt yuanfei/3.txt
- cp -r yuanfei feiyuan   拷贝目录及目录中所有内容

#### 2.5 mv命令

作用：移动文件或者目录

- mv 原文件名/目录名 新文件名/目录名 （剪切）

#### 2.6 通配符

- ~*~  匹配任意多个字符
  - rm *.txt：删除所有的后缀为txt的文件
  - rm y*：删除所有的以y开头的文件

- ~？~ 匹配一个字符
  - rm ?.txt 删除文件名中只有一个字符的txt文件

### 3. 显示文件内容

#### 3.1 cat命令

作用：显示文件内容在屏幕中

- cat 1.txt 在屏幕上显示1.txt的内容

#### 3.2 more和less命令

作用：分屏显示，比较适合显示超过一屏的长文本文件。

- more 1.txt
- less 1.txt
  - 按q键退出显示
  - 在less下，可以输入/关键字进行搜索

#### 3.3 head/tail命令

作用：显示文件头部/尾部10行的内容

- head 1.txt 显示头10行
- tail 1.txt 显示尾10行
- tail -n20 文件名 查看该文件末尾的20行，head同理

### 4、 搜索文件内容grep

作用：根据关键字搜索并且显示关键字所在的行

用法： grep [参数] 关键字 文件名

-  grep d 1.txt 	显示出d所在的行
- grep "d s" 1.txt      如果要查找的内容中间由空格，需要加引号（单引号或者双引号）
- grep -i "d s" 1.txt    忽略大小写查找，即大写的“D S”和小写的"d s"都可以查找到
- grep -v "D S" 1.txt    显示不匹配的行
- grep -n "d s" 1.txt     显示匹配的行的行号
- grep -c qhhsb! 1.txt     显示匹配的行的总数

## 三、 文件属性

### 1、 chmod改变文件的权限

[root@10 homework]# ls -l

~~~markdown
   u   g   o
- rw- r-- r--. 1 root root 555 11月  9 15:52 1.txt
- rw- r-- r--. 1 root root   6 11月  9 14:51 2.txt
d rwx r-x r-x. 2 root root   6 11月  9 14:59 feiyuan
d rwx r-x r-x. 2 root root  21 11月  9 15:06 yuanfei
~~~

第一列：表示是否是目录     -代表这是一个文件，d代表这是一个目录

第2-4列：用户的权限     当前登录的用户的权限

第5-7列：表示用户所在的用户组的权限group   当前用户的所在组的同组的人的权限

第8-10列：表示其他人的权限。除了同组人之外的所有人的权限。



r：read  可读  4

w：write  可写   2

x：execution  可执行   1

u：user

g：group

o：other

a：all 等价于ugo

=：表示赋值：指定给予某种权限，注意会覆盖原来的权限

+：add permission 添加权限

-：take away permission 移除权限

示例：

- chmod a+rwx 1.txt 给所有人(ugo)添加可读可写可执行的权限

- chmod go-w 1.txt 给所在的组合其他人移除写的权限

##### 数字表示法

chmod 724 1.txt 等价于 用户：rwx 所在组:w 其他人:r

即：r = 2^2   w = 2^1    x = 2^0    "-" = 0

## 四、查看进程

### 1、 ps命令

- 不带参数

~~~markdown
[root@10 homework]# ps
功能：查询在当前控制台上运行的进程
~~~

- 查看所有进程

~~~markdown
[root@10 homework]# ps -aux
功能：查询系统中所有运行的进程，包括后台进程，而且还可以显示出每个进程的父进程号。
~~~



### 2、 pstree命令（了解）

- 树状格式显示进程列表

~~~markdown
pstree
~~~



- 带进程号的树状格式显示进程列表

~~~markdown
pstree -p
~~~

### 3、 top命令(了解)

~~~shell
[root@10 homework]# top
~~~

动态的显示系统中的进程

### 4、 kill命令

- 杀掉指定进程

~~~markdown
[root@10 homework]# kill 708
~~~

- 强制杀掉指定进程

~~~markdown
[root@10 homework]# kill -9 708
~~~

补充：| 管道---链接两个命令的输入和输出，将一个命令的输出作为另一个命令的输入

~~~markdown
ps -ef | grep bash
查找包含bash的进程
~~~

## 五、 文本编辑器vi命令

### 1. 简介

~~~markdown
vi命令是UNIX操作系统和类UNIX操作系统中最通用的全屏幕的纯文本的编辑器。
vi编辑器由两种模式：编辑模式、命令行模式
vi 1.txt 进入编辑器，此时并不能编辑文本
需要通过输入【i/I、o/O、a/A、r/R】进入编辑模式，可修改文本文件
~~~

~~~markdown
1. i，I 进入输入模式(Insert mode)
	i为“从当前光标所在处输入”，I为“在目前所在行的第一个非空格字符处开始输入”。(常用)
2. a,A 进入输入模式(Insert mode)
	a为“从目前光标所在的下一个字符处开始输入“，A为”从光标的所在行的最后一个字符处开始输入“(常用)
3. o，O 进入输入模式(Insert mode)
	这是O的英文小写。o为“在目前光标的所在的行的下一行处输入新的一行”；O为“在目前光标在处的上一行输入新的一行”。
4. r(Replace mode)
	r只会取代光标所在位置的字符一次；R会一直取代光标所在位置的文字，直到按下esc为止。
~~~

### 2. 保存/退出

以下指令必须在命令行模式下输入

- :w  保存文本
- :q   不保存文本并退出vi
- :q!   不保存文本并强制退出vi

- :wq    保存文本并退出（常用）
- :wq!   强制退出并且保存

### 3. 删除、复制、粘贴、撤销

- 这些指令都必须在命令行模式执行
- dd：删除（剪切）光标所在的行
- ndd：删除（剪切）光标所在的行的向下的n行
- yy：复制当前行
- nyy：复制光标所在的向下的n行
- p：将已复制的数据在光标的下一行粘贴
- P：将已复制的数据在光标的上一行粘贴
- u：撤销
- shift+g：文件末尾
- shift+G：文件开头

## 六、 网络

### 1、 查看ip地址

~~~markdown
ifconfig
ip addr
~~~

### 2、 防火墙

- 查看防火墙状态

~~~shell
[root@10 homework]# systemctl status firewalld.service
~~~

- 关闭防火墙

~~~shell
[root@10 homework]# systemctl stop firewalld.service
~~~

- 开启防火墙

~~~shell
[root@10 homework]# systemctl start firewalld.service
~~~

### 3、 hosts设置

vi /etc/hosts

~~~markdown
127.0.0.1   localhost localhost.localdomain localhost4 localhost4.localdomain4
::1         localhost localhost.localdomain localhost6 localhost6.localdomain6
10.13.1.59 XX
~~~

## 七、 服务

### 1. 服务设置

~~~markdown
systemctl .... 服务名.service
~~~

### 2. 服务器开机自启动服务

- 列出所有系统的服务，并且检查是否开机启动

~~~shell
[root@10 homework]# systemctl list-unit-files --type service
~~~

- 服务开机不启动

~~~shell
[root@10 ~]# systemctl disable firewalld.service
~~~

- 服务开机启动

~~~markdown
[root@10 ~]# systemctl enable firewalld.service
~~~

## 八、 软件安装

### 1、 rpm命令

rpm这种软件包就好像是windows中的exe安装文件一样，各种文件已经编译好，并且打了包，哪个文件该放在哪个文件夹中，都指定好了。安装非常方便，在图形界面时，只需要双击就能安装。

- 查询所有已经安装的软件包的包名(q:查询 a:所有)

~~~markdown
rpm -qa
~~~

- 查询python软件包的安装位置(q:query l:location)

~~~markdown
rpm -ql python
~~~

- 查看已安装的软件的信息(i:info 信息)

~~~markdown
rpm -qi python
~~~

- 安装软件(i:install v:显示安装过程 h:显示安装细节)

~~~markdown
rpm -ivh xxxxxx.rpm
~~~

- 查看安装的软件的完整包名

~~~markdown
[root@10 ~]# rpm -qa | grep python
~~~

- 卸载软件(e)

~~~markdown
rpm -e 包名
~~~

### 2. tar命令

参数

- c 压缩文件
- x解压文件
- z格式为gzip
- v显示执行文件列表
- f要操作的文件

- 直接解压
  - tar -zxvf xxxx.tar 

一般来说tar包中都是已经编译好的文件，解压后可以直接使用；也存在一些tar包，在解压后需要进行编译，需要经过configure->make->make install

- 压缩

~~~markdown
tar -zcvf test.tar.gz /root/
将root目录中所有的文件压缩为test.tar.gz
~~~

### 3. Yum命令

基于RPM包管理，能够从指定的服务器自动下载RPM包并且进行安装。

Yum是CentOS独有的安装命令，需要外网环境，可以自动加载安装文件，及其所有依赖的资源，并且自动完成安装。

安装redis和nginx时可以采用。

### 4. 服务安装

#### mysql安装

Yum安装方式

~~~markdown
# 方式一
1. 在CentOS系统中，默认已经有了一个数据库，MariaDB，它是MySQL数据库的分支，如果要安装MySQL，首先必须要添加MySQL社区repo
		rpm -ivh http://repo.mysql.com//mysql57-community-release-el7-7.noarch.rpm
		rpm --import https://repo.mysql.com/RPM-GPG-KEY-mysql-2022
2. 再安装MySQL
		yum install -y mysql-server
~~~

~~~markdown
# 方式二：
	rpm -ivh ....rpm
	得下载mysql的rpm包，并且必须先安装mysql的所有依赖，然后再安装mysql的rpm包，否则安装失败。
~~~

#### 启动mysql的服务

~~~markdown
systemctl start mysqld
~~~

#### 修改mysql密码

~~~markdown
# mysql在yum安装的时候，自动生成了一个临时密码，存放在了mysql的日志中
1. 在日志文件中查找临时密码
		[root@10 ~]# grep 'password' /var/log/mysqld.log 
2. 使用临时密码进入mysql
		mysql -uroot -p回车
		输入临时密码
3. 修改密码
		mysql> SET PASSWORD = PASSWORD("ROOT");
		一定会报错：ERROR 1819 (HY000): Your password does not satisfy the current policy requirements
		# 密码不符合mysql的安全策略
		
		# 解决方案：
			# 修改mysql的密码的安全等级
			a. mysql> set global validate_password_policy = 0;
			# 修改mysql密码的长度限制
			b.mysql> set global validate_password_length = 1;
		# 再次执行
			mysql> SET PASSWORD = PASSWORD("123456");
4. 再次进入mysql
		mysql -uroot -p123456
~~~

#### 远程链接mysql

- mysql默认没有开启远程连接的权限，需要手动开启权限

~~~markdown
# 远程连接失败
# 原因一：防火墙
# 原因二：不允许其他主机进行连接

# 开启mysql远程连接的权限
1. 进入到mysql数据库的mysql库中
		mysql> update user set host='%' where user = 'root';
2. 重新刷新权限
		flush privileges;
~~~

#### 安装python

##### 安装依赖

~~~markdown
1. 依赖
		yum -y install python-devel openssl-devel bzip2-devel zlib-devel expat-devel ncurses-devel sqlite-devel gdbm-devel xz-devel tk-devel readline-devel gcc
2. 开发工具包
		yum -y groupinstall "Development tools"
3. 安装python
		a. 先把python安装包放在文件夹中
		b. 解压该安装包，进入到解压后的目录中执行
		./configure --prefix=/usr/local/python3 --enable-shared CFLAGS=-fPIC
		检查依赖并且指定python的安装位置
		c. make
		d. make install 
~~~

#### 修改linux默认python版本

~~~markdown
1. 查看python3的所在位置
		/usr/local/python3

2. 将linux系统中原有的python进行重命名
		[root@10 python3]# mv /usr/bin/python /usr/bin/python2.7.5
3. 将python3的解释器软连接到/user/bin/python
		[root@10 bin]# sudo ln -s /usr/local/python3/bin/python3.8 /usr/bin/python
4. 如果输入python，报错
		python: error while loading shared libraries: libpython3.8.so.1.0: cannot open shared object file: No such file or directory
# 解决方案：
		[root@10 bin]# cp /usr/local/python3/lib/libpython3.8.so.1.0 /usr/lib64/
~~~

#### 将python配置到环境变量中

- 只有配置了环境变量pip才可以生效

~~~markdown
1. 进入配置文件
		vi /etc/profile
2. 添加配置，保存并且退出
		export PATH=$PATH:/usr/local/python3/bin
3. 让环境变量生效
		[root@10 bin]# source /etc/profile
4. 测试
		pip3 -V
5. 更新pip
		python3 -m pip install --upgrade pip
~~~

#### 恢复yum

此时yum不可用（yum依赖py2.7）

```shell
vi /usr/bin/yum
vi /usr/libexec/urlgrabber-ext-down

修改第一行文本
#! /usr/bin/python2.7.5
```



















































