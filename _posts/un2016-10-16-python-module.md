---
layout:     post
title:      python中的module和class
category: blog
description: 。。
---

module的理念和dicts很像。都是通过key找到value的映射。不过module存的是代码，而dicts存的是对象。dicts是通过[key]的方式获取对象，module是通过.key的方式获取代码。

module引入后，整个整个程序唯一。但是class可以创建多个对象，对象之间独立不干扰。

类的初始化和调用一个函数一样。

Getting Things from Things的三种方式：
		# dict style 	mystuff['apples']
		# module style mystuff.apples()	print mystuff.tangerine
		# class style	thing = MyStuff() thing.apples()	print thing.tangerine
	
	
	
