---
layout:     post
title:      在bash中嵌套执行java代码
category: blog
description: 在bash中嵌套执行jar包，jar包返回结果作为bash的一个判断条件。
---

## 场景描述

在bash脚本中需要执行java程序，java程序的执行结果影响bash的执行。    
java字符串s为空则bash脚本停止执行，否则继续执行。     

## bash中代码
要实现功能：jar包执行，返回0则bash脚本停止执行，否则bash继续执行。
bash中代码如下：   

	java -jar switch.jar
	switch=$?
	if [ $switch -eq 0 ]; then
	        echo "stop execute"
	        exit -1
	fi

## Java代码   
要实现功能：如果字符串s为空，则返回0，否则返回1。
java代码：

	String s = "test";
	int exitCode = 0;
	try {
	    if (s != null)
	        exitCode = 1;
	} catch (Exception e) {}
	System.exit(exitCode);
	
上面只是举了个简单的例子，更丰富的功能可以自己在java代码和bash脚本中丰富，比如字符串s可以是另一个段java代码的返回值等等。   

（完）