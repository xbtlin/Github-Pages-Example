---
layout:     post
title:      Mysql中的between用法
category: blog
description: Mysql中的between用法
---

## between的用法

	SELECT column_name(s)
	FROM table_name
	WHERE column_name
	BETWEEN value1 AND value2  
	
mysql中是包括value1和value2的，也就是说是闭区间。
