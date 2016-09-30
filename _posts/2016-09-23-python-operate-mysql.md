---
layout:     post
title:      python操作MySQL
category: blog
description: python操作MySQL
---


安装MySQLdb遇到问题
TODO总结



	import MySQLdb
	db = MySQLdb.connect($DB_URL,$USERNAME,$PASSWORD,$DB_NAME,port=$PORT)

如果DB_URL=xxx.abc.com，USERNAME=aaa，PASSWORD=bbb，DB_NAME=ccc，PORT=5002。
则连接数据库语句为

	db = MySQLdb.connect("xxx.abc.com","aaa","bbb","ccc",port=5002)



插入数据：
	
works!
	
#!/usr/bin/python
# -*- coding: UTF-8 -*-

import MySQLdb

# 打开数据库连接
db = MySQLdb.connect("dx-dataapp-mysql-datatools01","ttpj","Impq55}Y_DHr,=","ttpj_db",port=5002)

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