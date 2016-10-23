---
layout:     post
title:      MySQL
category: blog
description: ..
---

UNIX时间戳转换为日期用函数： FROM_UNIXTIME()

	select FROM_UNIXTIME(1156219870);
日期转换为UNIX时间戳用函数： UNIX_TIMESTAMP()

	select UNIX_TIMESTAMP(’2006-11-04 12:23:00′);