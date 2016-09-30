---
layout:     post
title:      python中的join和split
category: blog
description: python中的join和split
---

1.join用法示例 
	
	>>>li = ['my','name','is','bob'] 
	>>>' '.join(li) 
'my name is bob' 
 
	>>>'_'.join(li) 
'my_name_is_bob' 
 
	>>> s = ['my','name','is','bob'] 
	>>> ' '.join(s) 
'my name is bob' 
 
	>>> '..'.join(s) 
'my..name..is..bob' 
 
2.split用法示例 

	>>> b = 'my..name..is..bob' 
 
	>>> b.split() 
['my..name..is..bob'] 
 
	>>> b.split("..") 
['my', 'name', 'is', 'bob'] 
 
	>>> b.split("..",0) 
['my..name..is..bob'] 
 
	>>> b.split("..",1) 
['my', 'name..is..bob'] 
 
	>>> b.split("..",2) 
['my', 'name', 'is..bob'] 
 
	>>> b.split("..",-1) 
['my', 'name', 'is', 'bob'] 
 
可以看出 b.split("..",-1)等价于b.split("..") 