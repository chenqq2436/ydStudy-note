#### 操作系统和后端知识
1. 两种安装包格式
    * rpm centos redhat fedora 
    * deb ubuntu debian
2.  mac是基于unix 
3. sudo命令用于提升权限
4. 行编辑器 vi/vim
    * i 进入插入模式
    * esc退出插入模式 :wq 保存并退出
    * q! 不保存并退出
    * /用于检索 n继续寻找下一个 N 或 shift + n寻找上一个 i用于退出检索模式
    * ifconfig == windows -> ipconfig
    * pwd 查看当前所在路径
    * 命令行下载命令
        + curl （功能更加强大 使用繁琐）
        + wget 下载地址 （使用简单）
    * brew 、yum 、apt-get 命令行的软件商店的客户端
    *  --hellp查看帮助命令
    * man 命令 查看详细的解释文档
    * ctrl + s 会将终端挂起 
        * 解决方法 ctrl + q
    * ctrl + a 或者 ctrl + e 快速切换到行头 或 行尾
    * yum erase xxxxxx
5. 服务管理命令 systemctl
------
##### 远程登录
1. ssh的通信是被加密的
    + ssh root@ip地址（服务器名称）
2. #说明是用户管理员权限非常大 $说明是普通用户
