---
layout:     post
title:      动手写个简单的前端
category: blog
description: 一个数据可视化的前端。
---

## 为什么不显示图形   
图形所在的div一定要指定长宽才能正确显示。   
	
	<div id="pie-orders-category" style="width: 200px; height: 200px"></div> 
	
如果没有

	style="width: 200px; height: 200px"  
	
那么图形是无法显示的。

## Chrome环境的Tips   
针对Mac电脑
`F10`单步调试，遇到函数跳过。   
`F11`单步调试，遇到函数进入。  
`F8`继续执行代码，直到遇到另一个断点。  
`Ctrl+R`刷新页面。OSX系统是`Cmd+R`。   
全局查找很有用，快捷键不同电脑不一样，可以通过右上角的`Setting-Shortcuts`查看。OSX默认应该是`Cmd+Alt+F`。   
可以直接在js页面上打断点，调试起来方便。    
可以在Console中执行js命令。   
修改前端页面，只需要保存文件，并刷新页面就可以了，不需要重启服务器。   
引用jquery，echarts等，可以直接google jquery + cdn 可以找到在线加载的地址。    
[Chrome开发工具指南](http://wiki.jikexueyuan.com/project/chrome-devtools/debugging-javascript.html)

## jQuery时间-ready()方法   
在文档加载后激活函数：    

	$(document).ready(function(){...})    
	
可以简写成：   

	$(function(){...})

可以叫自执行匿名函数。是jQuery中很重要的一句话，所有页面载入有执行的代码都要写这个语句。   

其他写法：  

	(function () { /* code */ } ()); 
!function () { /* code */ } ();
~function () { /* code */ } ();
-function () { /* code */ } ();
+function () { /* code */ } ();    


## 定时执行js函数  
把函数作为参数传到setInterval()函数中： 

	  setInterval(myFucntionName, interval)
	 
interval是以毫秒为单位的。     







