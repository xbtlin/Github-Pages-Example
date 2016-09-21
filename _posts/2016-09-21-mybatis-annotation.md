---
layout:     post
title:      Mybatis基于注解的方式
category: blog
description: Mybatis基于注解的方式。
---


Mybatis基于注解的方式：     

	 @Select("select dt,count(*) as count from poi_discount_d group by dt " +
            "where dt >= #{start} and dt <= #{end} group by dt order by dt")
    List<Map> getTrend(@Param("start") String start, @Param("end") String end);    
   
注意参数之前加的`@Param()`如果不加这个，那么只能通过`param1`这种方式在sql中引用，而不能通过`start`这种有含义的字符串。   