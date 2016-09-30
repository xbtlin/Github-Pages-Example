---
layout:     post
title:      hdfs的常用命令
category: blog
description: hdfs的常用命令
---

在linux命令行或者bash脚本中

首先定义一些变量
	
	HDFS="/opt/meituan/hadoop/bin/hdfs"
	data_output_path="/user/hadoop-mining/linxuan02/unreception_detection"
	
用于检测文件或者文件夹是否存在

	$HDFS dfs -test -e $data_output_path"/dt="$data_date
	
删除文件或文件夹
	
	$HDFS dfs -rm -r $data_output_path"/dt="$data_date"/filtered_unreception_"$data_date
	
The -R/-r option deletes the directory and any content under it recursively.	
	
创建文件夹

	$HDFS dfs -mkdir $data_output_path"/dt="$data_date
	
从远程获取文件到本地文件夹

	$HDFS dfs -get $data_input_path"/dt="$data_date"/*" ./
	
将本地文件放到远端hdfs文件系统上

	$HDFS dfs -put "./data/filtered_unreception_"$data_date $data_output_path"/dt="$data_date
	
	
在linux中如果存在一个file名字叫filename1，那么就无法创建一个同名的文件夹。dfs中也是如此。
