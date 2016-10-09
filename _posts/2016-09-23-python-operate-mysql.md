---
layout:     post
title:      python操作MySQL
category: blog
description: python操作MySQL
---
        

首先需要引入MySQLdb包，如果出现`ImportError: No module named ***`，则需要用`pip install MySQL-python`安装MySQLdb包。`pip`是安装Python时自带的命令。

	import MySQLdb
	db = MySQLdb.connect($DB_URL,$USERNAME,$PASSWORD,$DB_NAME,port=$PORT)

例如，DB_URL=xxx.abc.com，USERNAME=aaa，PASSWORD=bbb，DB_NAME=ccc，PORT=5002。
则连接数据库语句为

	db = MySQLdb.connect("xxx.abc.com","aaa","bbb","ccc",port=5002)
	
	db = MySQLdb.connect("localhost","root","","houseprice",port=3306) 
   sql = "INSERT INTO test VALUES (677777)"      

插入数据：
	
	import MySQLdb

	# 打开数据库连接
	db = MySQLdb.connect("dx-dataapp-mysql-datatools01","ttpj","xxxx","ttpj_db",port=5002)

	# 使用cursor()方法获取操作游标 
	cursor = db.cursor()

	# SQL 插入语句
	sql = """INSERT INTO unreception_deals_d(deal_id,
	         dt)
	         VALUES (677777,"20160912")"""
	try:
	   # 执行sql语句
	   cursor.execute(sql)
	   # 提交到数据库执行
	   db.commit()
	except:
	   # Rollback in case there is any error
	   db.rollback()

	# 关闭数据库连接
	db.close()   
	
上面是插入数据，查询、删除、修改同理。只需要把sql改变即可。    

（完）