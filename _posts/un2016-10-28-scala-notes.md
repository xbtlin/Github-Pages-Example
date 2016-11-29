---
layout:     post
title:      Scala
category: blog
description: ..
---

Scala 是一门类 Java 的编程语言，它结合了面向对象编程和函数式编程。

## 变量赋值
val vs var?
在 Scala 中，使用关键词 "var" 声明变量，使用关键词 "val" 声明常量。
Scala有两种变量，val和var。val就不能再赋值了。与之对应的，var可以在它生命周期中被多次赋值。
声明变量的方式：
var myVar : String = "Foo"
或 var myVar="Foo" ，这时myVar被推断为String类型。

变量声明不一定需要初始值，以下也是正确的：   
val myVal :String;

var xmax, ymax = 100  // xmax, ymax都声明为100


## 函数  
Scala 有函数和方法，二者在语义上的区别很小。Scala 方法是类的一部分，而函数是一个对象可以赋值给一个变量。换句话来说在类中定义的函数即是方法。     
Scala 函数名可以由以下特殊字符：+, ++, ~, &,-, -- , \, /, : 等。    

Scala 函数声明格式如下：
def functionName ([参数列表]) : [return type]     

方法定义由一个def 关键字开始，紧接着是可选的参数列表，一个冒号"：" 和方法的返回类型，一个等于号"="，最后是方法的主体。
Scala 函数定义格式如下：

	def functionName ([参数列表]) : [return type] = {
		function body
		return [expr]
	}
	
如果函数没有返回值，可以返回为 Unit，这个类似于 Java 的 void    

## 类   
object和class的区别。    
You can think of the object keyword as creating a singleton object of a class that is defined implicitly.     




