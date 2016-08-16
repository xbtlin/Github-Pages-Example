---
layout:     post
title:      bash的控制语句
category: blog
description: bash中的控制语句，比如if else, while, for, until。
---

### if...then...else   
看一个简单的例子：    
	
	#!/bin/bash
	# testarg

	if [ $# -eq 2 ]
	then
		echo arguments right
	elif [ $# -gt 2 ]
	then
		echo arguments should not more that 2.
	else
		echo arguments should not less that 2.
	fi

	echo the argument is $#
	exit 0
解释上段代码，`$# -eq 2`意思是参数的数量等于2，`-eq`表示等于，是equal的缩写，`-gt`表示大于，是great的缩写。   
if语句中需要注意的是：    
	
	1. if 与[ 之间必须有空格
	2. [ ]与判断条件之间也必须有空格

更多if的判断条件语句整理：   

	-z $1 判断是否有参数   
	-f $1 判断参数1是否是文件    
	-d $1 判断参数1是否是目录   

### while    
看个简单的例子

	#!/bin/bash
	
	while ps aux | grep $1
	do 
		sleep 1
	done
	
	logger $1 is no longer present
	exit 0

上段代码比较直观，while后面跟的是条件判断语句，如果条件判断语句成立，则执行do语句。上面代码中，如果ps aux中包含参数1，则激活while的do语句，否则跳过while。其中ps命令用于查看进程状态，是process status的缩写。aux是ps命令的参数。可以通过在命令行中`man ps`查看含义。|是管道符，grep代表字符串匹配。    

### for
直接看例子

	!/bin/bash
	# counter
	
	for (( counter=1; counter<10; counter++ )); do
		echo "The counter is now set to $counter"
	done
	
	exit 0
比较好懂。


### until      
until和while是相反的。一个简单的例子：   
	
	!/bin/bash
	
	until who | grep $ 1 >> /dev/null
	do
		echo $1 is not logged in yet
		sleep 5
	done 
	
	echo $1 has just logged in
	
	exit 0
	
在上述代码中，`who | grep $1`循环执行，只要参数1不在用户列表中，则就不停执行。直到参数1的用户在用户列表中，则停止执行until循环。   


	                                                                                                                                                                             