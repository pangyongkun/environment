#	<center> turn服务器搭建 </center>

##	1.搭建说明

搭建平台：ubuntu16.04
使用开源软件：coturn
说明：coturn是免费开源的TURN和STUN Server
开源地址：https://github.com/coturn/coturn 

##	2.安装依赖
依赖包：

debhelper (>= 9.0.0)

dpkg-dev (>= 1.16.1~)

libssl-dev (>= 1.0.0~)

libevent-dev (>= 2.0.1~)

postgresql-client
	
libpq-dev

mysql-client

libmysqlclient-dev

libhiredis-dev

这里我把所有的一起安装了：

	sudo apt-get install debhelper dpkg-dev libssl-dev libevent-dev postgresql-client libpq-dev mysql-client libmysqlclient-dev libhiredis-dev

##	3.下载coturn


	#使用git下载源码包
	git clone git://git.debian.org/pkg-voip/coturn.git
##  4.编译安装

###  1）进入到coturn文件夹
	cd coturn
###  2）执行configure,我觉的有必要切换成root，我安装时用的是root权限安装的
	./configure 
这一步会生成makefile文件
###  3）编译
	make
###	 4）安装
	make install
这一步安装后给出提示操作，配置服务器的一些权限和参数，良心建议仔细看。
##  5.配置服务器
	vi /etc/turnserver.conf
这里我只是简单配置，把监听端口打开了:

![Alt path]('turnserver_install.png')

还有好多权限配置，有兴趣可以自己配一下

##  6.启动服务器

	./usr/local/bin/turnserver

这样服务器就启动了

##  7.经过代码测试,我的服务器搭建成功
友情提示：我的服务器部署在阿里云上，阿里云有安全组限制，你得把相应的端口打开，不然会被访问拒绝的。




