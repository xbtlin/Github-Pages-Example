---
layout:     post
title:      在ETL平台开发mysql表和hive表的差异
category: blog
description: 在ETL平台开发mysql表和hive表的差异
---


| hive               | MySQL |
|--------------------|-------|
| 需要Insert overwrite | 不需要   |
| COMMENT没有=符号       | 有     |
|字符串用string| 字符串用varchar|
主体写在##LOAD##中|主体写在Extract中



kerberos认证
