---
layout:     post
title:      awk合并多个文件并去除重复行
category: blog
description: awk合并多个文件并去除重复行。
---

在awk中一行代码就能实现：    

	awk '!a[$0]++' a.txt b.txt c.txt    
	

第一列重复的，保留任意一行。

	awk '!a[$1]++ ' a b c
	
	
	
	
	awk '/pattern/ {action}' file1 file2 file3 > file4
	
	
	
	
sed中如何用\t？    
TAB=$'\t'    
${TAB}代表

cut: weekdata1: Illegal byte sequence    
在命令前面加