---
layout:     post
title:      HTML/CSS/JS学习笔记
category: blog
description: HTML/CSS/JS学习笔记
---

## HTML块元素和内联元素   
大都数HTML元素分为块元素（block level element）和内联元素(inline element)。    
块元素在浏览器显示时，通常以新行来开始（和结束）。块元素例子：`<h1>, <p>, <ul>, <table>`。    
内联元素通常不会以新行开始，例子：`<b>, <td>, <a>, <img>`    


## `<div>`和`<span>`
`<div>`是块级元素，是用于组合其他HTML元素的容器，用于内容块设置样式属性。可用于文档布局。     
`<span> `元素是内联元素，可用作文本的容器，用于为部分文本设置样式属性。

## HTML`<div>`标签    	
`<div>`标签定义位于HTML文档中的区或节(division or section)    
`<div>`用于将块元素分组，常与CSS一起用于网页布局。   

## $符号作用   
[stackoverflow回答1](http://stackoverflow.com/questions/205853/why-would-a-javascript-variable-start-with-a-dollar-sign)    
[stackoverflow回答2](http://stackoverflow.com/questions/3107543/what-is-the-symbol-used-for-in-javascript)   
我个人理解是$可以作为引用函数的简写。     

## array.push()   
先看一段代码：

	<!DOCTYPE html>
	<html>
	<body>

	<p>Click the button to add a new element to the array.</p>

	<button onclick="myFunction()">Try it</button>

	<p id="demo"></p>

	<script>
	var fruits = ["Banana", "Orange", "Apple", "Mango"];
	document.getElementById("demo").innerHTML = fruits;

	function myFunction() {
	    fruits.push("Kiwi");
	    document.getElementById("demo").innerHTML = fruits;
	}
	</script>

	</body>
	</html>
点击按钮，会在数组后面不断添加字符串`Kiwi`。     
push的意思是在数组后面插入，类似于append。    

## 在js中发ajax请求    
ajax不是编程语言，只是一种创建更好交互web应用的技术。   
[jQuery Ajax操作函数](http://www.w3school.com.cn/jquery/jquery_ref_ajax.asp)   
重点说一下ajax()方法    
ajax() 方法通过 HTTP 请求加载远程数据。    
该方法是 jQuery 底层 AJAX 实现。简单易用的高层实现见 $.get, $.post 等。$.ajax() 返回其创建的 XMLHttpRequest 对象。大多数情况下你无需直接操作该函数，除非你需要操作不常用的选项，以获得更多的灵活性。     
最简单的情况下，$.ajax() 可以不带任何参数直接使用。     
ajax()方法的[详细参数列表](http://www.w3school.com.cn/jquery/ajax_ajax.asp)     

简单说几个常用的参数：   

	- url
		类型：String
		默认值: 当前页地址。发送请求的地址。
	
	- type   
		类型：String
		默认值: "GET"。请求方式 ("POST" 或 "GET")， 默认为 "GET"。注意：其它 HTTP 请求方法，如 PUT 和 DELETE 也可以使用，但仅部分浏览器支持。    
		
	- dataType    
		类型：String
		预期服务器返回的数据类型。如果不指定，jQuery 将自动根据 HTTP 包 MIME 信息来智能判断，比如 XML MIME 类型就被识别为 XML。在 1.4 中，JSON 就会生成一个 JavaScript 对象，而 script 则会执行这个脚本。随后服务器端返回的数据会根据这个值解析后，传递给回调函数。可用值:
		"xml": 返回 XML 文档，可用 jQuery 处理。
		"html": 返回纯文本 HTML 信息；包含的 script 标签会在插入 dom 时执行。
		"script": 返回纯文本 JavaScript 代码。不会自动缓存结果。除非设置了 "cache" 参数。注意：在远程请求时(不在同一个域下)，所有 POST 请求都将转为 GET 请求。（因为将使用 DOM 的 script标签来加载）
		"json": 返回 JSON 数据 。
		"jsonp": JSONP 格式。使用 JSONP 形式调用函数时，如 "myurl?callback=?" jQuery 将自动替换 ? 为正确的函数名，以执行回调函数。
		"text": 返回纯文本字符串

	- success  
		类型：Function
		请求成功后的回调函数。
		参数：由服务器返回，并根据 dataType 参数进行处理后的数据；描述状态的字符串。
		这是一个 Ajax 事件。    
		

## `<!DOCTYPE>`标签   
<!DOCTYPE>声明必须是HTML文档的第一件事，在`<html>`标签之前。     
<!DOCTYPE>不是HTML标签，而是用于告诉浏览器HTML页面是用哪个版本的HTML写的。    
在HTML4.01中，<!DOCTYPE>需要引用DTD，因为 HTML4.01 基于SGML。    
HTML5不基于SGML，所以不需要应用DTD。  
HTML5中：

	<!DOCTYPE html> 
	
HTML4的传统定义: 
	
	<!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN" "http://www.w3.org/TR/html4/loose.dtd">    
		
出了传统定义，还严格定义、Frameset定义。只需要将上面代码的`loose.dtd`分别改成`strict.dtd`和`frameset.dtd`就好。     

浏览器通过<!DOCTYPE>声明来决定如何渲染网页。所以一定要写！   

## JS对象   
JavaScript 中的所有事物都是对象：字符串、数值、数组、函数...    
此外，JavaScript 允许自定义对象。   
JavaScript 提供多个内建对象，比如 String、Date、Array 等等。
对象只是带有属性和方法的特殊数据类型。     
访问对象属性的语法是：    

	objectName.propertyName      

您可以通过以下语法来调用方法：    

	objectName.methodName()    
	
## 创建JS对象    
**直接创建**    

	person=new Object();
	person.firstname="Bill";
	person.lastname="Gates";
	person.age=56;
	person.eyecolor="blue";

或这种形式   

	person={firstname:"John",lastname:"Doe",age:50,eyecolor:"blue"};   
	
**使用对象构造器**

	function person(firstname,lastname,age,eyecolor)
	{
	this.firstname=firstname;
	this.lastname=lastname;
	this.age=age;
	this.eyecolor=eyecolor;
	}   
	
用对象构造器穿件新的对象实例：    

	var myFather=new person("Bill","Gates",56,"blue");    
	
## 把属性添加到 JS 对象    
您可以通过为对象赋值，向已有对象添加新属性：

	person.firstname="Bill";
	person.lastname="Gates";
	person.age=56;
	person.eyecolor="blue";

## 把方法添加到JS对象   

	function person(firstname,lastname,age,eyecolor)
    {
    this.firstname=firstname;
    this.lastname=lastname;
    this.age=age;
    this.eyecolor=eyecolor;

    this.changeName=changeName;
    function changeName(name)
    {
    this.lastname=name;
    }
    }     
    
JavaScript 是面向对象的语言，但 JavaScript 不使用类，因为JavaScript 基于 prototype，而不是类。   

## JS for...in循环    
JavaScript for...in 语句循环遍历对象的属性。

	for (对象中的变量)
	{
	要执行的代码
	}   
	
	
## JS HTML DOM   
通过 HTML DOM，可访问 JavaScript HTML 文档的所有元素。     
当网页被加载时，浏览器会创建页面的文档对象模型（Document Object Model）。    
HTML DOM 模型被构造为对象的树。     
具体见[HTML DOM](http://www.w3school.com.cn/js/js_htmldom.asp)    
可以通过元素的id、标签名和类型找到HTML元素。    
JS能够改变页面中所有的HTML元素、HTML属性、CSS样式、对页面的所有事件做出反应。   
  
**改变 HTML 内容**
修改 HTML 内容的最简单的方法时使用 innerHTML 属性。   

	document.getElementById(id).innerHTML=new HTML   
	
**改变 HTML 样式**   
如需改变 HTML 元素的样式，请使用这个语法：

	document.getElementById(id).style.property=new style
 
## 两个div位置关系   

想让两个div的位置是上下关系，可用float:left标签，不过不理解为啥。
