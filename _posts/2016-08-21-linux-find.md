---
layout:     post
title:      Linux的查找命令
category: blog
description: Linux查找某个文件，查找包含特定字符串的文件名
---

## Linux查找某个文件  
   
### find   

find是最常见和最强大的查找命令，你可以用它找到任何你想找的文件，但是时间花费也多，因为find是直接查找硬盘。    
find的使用格式如下：    
	
	$ find <指定目录> <指定条件> <指定动作>    
	- <指定目录>： 所要搜索的目录及其所有子目录。默认为当前目录。   
	- <指定条件>： 所要搜索的文件的特征。   
	- <指定动作>： 对搜索结果进行特定的处理。
	
如果什么参数也不加，find默认搜索当前目录及其子目录，并且不过滤任何结果（也就是返回所有文件），将它们全都显示在屏幕上。      

find的使用实例：     
	
	$ find . -name 'yy*'   

搜索当前目录（含子目录，以下同）中，所有文件名以yy开头的文件。　   

### locate    

locate命令其实是"find -name"的另一种写法，但是要比后者快得多，原因在于它不搜索具体目录，而是搜索一个数据库（/var/lib/locatedb），这个数据库中含有本地所有文件信息。Linux系统自动创建这个数据库，并且每天自动更新一次，所以使用locate命令查不到最新变动过的文件。为了避免这种情况，可以在使用locate之前，先使用`sudo updatedb`，手动更新数据库。这儿加一句，Mac电脑下的等价命令是`sudo /usr/libexec/locate.updatedb`。

locate命令的使用实例：
	
	$ locate ~/m	
	
搜索用户主目录下，所有以m开头的文件。

### whereis    

whereis命令只能用于程序名的搜索，而且只搜索二进制文件（参数-b）、man说明文件（参数-m）和源代码文件（参数-s）。如果省略参数，则返回所有信息。whereis也是搜索数据库，速度很快。
whereis命令的使用实例：　
	
	$ whereis grep

### which  
which命令根据PATH变量指定的路径中，搜索某个系统命令的位置，并且返回第一个搜索结果。也就是说，使用which命令，就可以看到某个系统命令是否存在，以及执行的到底是哪一个位置的命令。
which命令的使用实例：		
		
	$ which grep

### Linux查找包含特定字符串的文件名的方法   

考虑一种特殊场景，即查找包含某个特定字符串的文件。这需要联合使用 find、xargs 和 grep 命令才能达到目的。

通过下面这个命令组合，就可以查找当前目录以及其子目录中，所有包含 “meituan” 这个字符串的文件。
示例：

	find . |xargs grep "meituan"   

延伸一下，通过下面这个命令组合，查找当前目录以及其第一级子目录中，所有包含 “meituan” 这个字符串的文件。
示例：

	find . -maxdepth 2|xargs grep "VPSeek"   

进而，通过使用下面这个命令组合，查找当前目录以及其第一级子目录中，所有以 “.txt” 结尾并且包含 “meituan” 这个字符串的文件。
示例：

	find . -maxdepth 2 -name "*.txt" |xargs grep "meituan"  	
(完)


	                                                                                                                                                                             