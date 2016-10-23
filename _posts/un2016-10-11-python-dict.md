---
layout:     post
title:      python学习笔记-字典
category: blog
description: python学习笔记-字典
---

python的字典（dicts）相当于java或c++中的hash，dicts是无序的。如果想要有序字典，用OrderedDict。

python的key和value可以是数字、字符串等。python中没有char类型。

关于python的print中占位符，dict的遍历

	states = [
		'Oregon': 'OR',
		'Florida': 'FL', 
		'California': 'CA', 
		'New York': 'NY', 
		'Michigan': 'MI'
	]
	print '_' * 10
	print "Michigan's abbreviation is: ", states['Michigan']
	for state, abbrev in states.items():		print "%s is abbreviated %s" % (state, abbrev)
输出为:
	__________
	Michigan's abbreviation is: MI
	California is abbreviated CA 
	Michigan is abbreviated MI 
	New York is abbreviated NY 
	Florida is abbreviated FL 
	Oregon is abbreviated OR
	
