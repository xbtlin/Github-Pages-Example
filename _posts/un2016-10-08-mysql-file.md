---
layout:     post
title:      MySQL中的数据是如何存储的
category: blog
description: MySQL中的数据是如何存储的
---

MySQL中一个数据库、表在文件系统中是什么样子呢？    

TODO


问题：
Sequel Pro 1.0.1 encountered an unexpected error when connecting to mysql 5.7.13  

解决办法，运行下面得命令升级mysql，重启服务就好了 The fix was to run:  

	mysql_upgrade -u root -p  
	mysql.server restart  

