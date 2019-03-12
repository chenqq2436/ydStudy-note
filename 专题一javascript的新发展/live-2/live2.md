* opt目录时用户自己的安装目录
* shutdown now -h 关机
* Ubuntu 下载的安装包是deb格式 centos rpm
* centos下载命令: yum Ubuntu 下载命令：apt-get
mac 下载命令：brew
* http 默认端口80 https 443 mysql 3306
* pid 和 port 不是一个概念
* windows可以下载xshell、putty 终端软件
* 添加官方的yum源
curl -sL https://rpm.nodesource.com/setup_11.x 
bash - 
* yum命令安装
yum install -y nodejs
*#* 查看安装的版本
node -v
* ls 列出所有文件和文件夹
#### 各种文件夹对应的功能
1. bin 
    * 存放操作系统的各种命令
    * linux脚本文件的后缀为sh
    * ls -l列出所有文件 文件名最后有-x的都是可执行的
2. etc
    * 存放各种配置文件和脚本
3. dev
    * 开发所用的东西
4. home
    * 存放多用户的文件 -- windows c:\\\\user
5. lib lib64 -- windows >c:\\\\windows
    * 存放系统的二进制库
6. media mnt 
    * 用户接上u盘或软盘在这里面找
7. proc
    * 存放动态数据（实际上是在内存中）
8. boot 
    * 系统引导文件(内核)
9. opt 
    * 用户自己安装软件的安装位置

#### 命令
1. 解压命令
    tar -zxvf xxx.tar.gz
    tar -xvvf xxx.tar.bz
2. /根目录 ~用户目录
3. mkdir创建文件夹 touch创建文件