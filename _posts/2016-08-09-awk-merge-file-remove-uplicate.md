---
layout:     post
title:      awk合并多个文件并去除重复行
category: blog
description: awk合并多个文件并去除重复行，顺便整理点别的。
---

合并a,b,c三个文件，重复行只保留1份。在awk中一行代码就能实现：    

	awk '!a[$0]++' a b c    
	
上面衡量行重复的标准是，行之间完全重复。如果想实现某一列重复，则任意保留一份，则用下面的语句：   
例：第一列重复的，保留任意一行。

	awk '!a[$1]++ ' a b c	

sed中如何用\t？    
	
	TAB=$'\t'    
	用${TAB}代表\t

如果遇到类似的错误Illegal byte sequence咋办    

	在命令前面加LC_ALL=C