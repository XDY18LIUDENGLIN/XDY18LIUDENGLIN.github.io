---
title: MySQL安装与配置
cover: 'https://landeng-image.oss-cn-hangzhou.aliyuncs.com/img/wallhaven-13jg59.jpg'
tags:
  - MySQL
  - 数据库
background: >-
  url(https://landeng-image.oss-cn-hangzhou.aliyuncs.com/img/64710934_p0_master1200.jpg)
description: 将本站针对butterfly主题的亿点点小改动做个集锦。
swiper_index: 8
abbrlink: 8ae56098
date: 2022-11-10 23:49:54
---
## 下载MySQL压缩包
[MySQL8.0下载](https://dev.mysql.com/downloads/mysql/ "MySQL8.0下载")
[MySQL5.7下载](https://downloads.mysql.com/archives/community/ "MySQL5.7下载")
## 配置文件 
新建data目录和my.ini文件
![](https://landeng-image.oss-cn-hangzhou.aliyuncs.com/img/20220630134746.png)
修改my.ini文件用记事本打开my.ini 放入如下代码（basedir 和 datadir 的路径根据自己设置）。
```shell
[mysql]
# 设置mysql客户端默认字符集
default-character-set=utf8 
[mysqld]
#设置3306端口
port = 3306 
# 设置mysql的安装目录
basedir=D:\CODE-IDE\MySQL\mysql-5.7.32-winx64
# 设置mysql数据库的数据的存放目录
datadir=D:\CODE-IDE\MySQL\mysql-5.7.32-winx64\data
# 允许最大连接数
max_connections=200
# 服务端使用的字符集默认为8比特编码的latin1字符集
character-set-server=utf8
# 创建新表时将使用的默认存储引擎
default-storage-engine=INNODB
skip-grant-tables
```
## 修改环境变量
==在环境变量加入mysql的bin路径==
![](https://landeng-image.oss-cn-hangzhou.aliyuncs.com/img/20220630135457.png)

![](https://landeng-image.oss-cn-hangzhou.aliyuncs.com/img/20220630135550.png)

初始化mysql
切换到mysql的bin目录
`mysqld --initialize`
![](https://landeng-image.oss-cn-hangzhou.aliyuncs.com/img/20220630135805.png)
```
如果此处报错 Can't create/write to file 。。
将my.ini文件如二 中的 basedir 和 datadir 路径见引号和双斜杠&emsp;
# 设置mysql的安装目录
basedir="D:\\tool\\Mysql\\mysql-5.7.26-winx64"
# 设置mysql数据库的数据的存放目录
datadir="D:\\tool\\Mysql\\mysql-5.7.26-winx64\\data"
```

`输入 mysqld --install`

![](https://landeng-image.oss-cn-hangzhou.aliyuncs.com/img/20220630140124.png)
```
输入 net start mysql         启动服务
输入mysql -u root -p  回车  不用输入密码   继续回车进入数据库
输入 use mysql
输入  update mysql.user set authentication_string=password('123456') where user='root';    
将修改 mysql中的 my.ini文件  删掉最后一行的代码（跳过表验证）skip-grant-tables
重启服务（要切换到mysql的bin目录！！！！！！！！）   
net stop mysql
net start mysql
```

![](https://landeng-image.oss-cn-hangzhou.aliyuncs.com/img/20220630140251.png)