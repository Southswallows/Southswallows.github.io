---
layout: post
title: Mysql在Mac中安装
category: 技术
tags: web
keywords: 
description: 
---

![MySql](http://7xkeeu.com1.z0.glb.clouddn.com/mysql.jpg)


>MySQL是一款开源的数据库软件，被广泛的运用

**[官网地址](http://www.mysql.com)**

----

###1. 下载MySQL

[点击进入下载界面](http://dev.mysql.com/downloads/mysql/)

**下载MySQL Community Server，**此版本是免费版。

有*TAR*格式和*DMG*格式，选择简单的**DMG**格式进行安装。

###2. 双击mysqlxxx.dmg文件

**无需设置，一步一步进行下去，直到Finish**

**MySQL Community Server安装完毕,可在系统偏好设置里发现MySQL的图标**

![](http://7xkeeu.com1.z0.glb.clouddn.com/mysql-1.png)

###3. Start MySQL Server

点击MySQL图标，再点击右边的Start MySQL Server按钮

**数据库就运行了**

###4. shell中运行MySQL

打开终端，在`.bash_profile`或者`.zshr`中添加如下代码

		export PATH=$PATH:/usr/local/mysql/bin
**根据使用的shell不同，在不同文件中添加**

###5. 运行

在终端中输入

		mysql -u root -p
**如果没有设置密码，直接按回车键**

###6. root密码修改

由于后面的使用需要保证root有密码。root默认密码为空

进入mysql界面之后，（如下图）

![mysql界面](http://7xkeeu.com1.z0.glb.clouddn.com/mysql-2.png)

输入

		set password for 'root'@'localhost'=password('newpasswd');
		其中newpassword是你需要设置的密码

