---
layout:     post
title:      js中操作Map数组替换文本
category: blog
description: js操作map数组替换文本。
---


java向js返回的List会自动转换成js中的数组Array。

## js的几种循环方式


## 在js中，给定一个Map，如何取到该Map的key的有序列表

	A={a:2,b:3}
	Object.keys(A).sort().map(function(key){ return A[key]})

## 在js中，给定一个Map，如何取到该Map的value的有序列表，和上面的key一一对应

	var res = [];
	var source = Object.keys(A).sort();

	for(i = 0; i < source.length; i++ ) {
		res.push(A[source[i]]);
	}


## js替换文本的几种方式
第一种：

	$("#div_id").text(content_xx);

第二种：

	x=document.getElementById("div_id");
	x.innerText或innerHTML = content_xx;




