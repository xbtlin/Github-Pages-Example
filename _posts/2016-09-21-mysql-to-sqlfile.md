---
layout:     post
title:      将线上数据库导出成*.sql文件
category: blog
description: 将线上数据库导出成*.sql文件，可用于将线上数据库导入到线下数据库。
---

## 将数据库导出成*.sql文件    

导出一张表：    
mysqldump -h'dx-dataapp-mysql-datatools01' -u'ttpj' -p'Impq55}Y_DHr,=' -P5002 ttpj_db  poi_discount_d --skip-lock-tables  > poi_discount_d.sql     

导出一张表的一部分：     
mysqldump -h'dx-dataapp-mysql-datatools01' -u'ttpj' -p'Impq55}Y_DHr,=' -P5002 ttpj_db  ttpj_alert --where " created_time > '2015-11-20 00:00:00' limit 15000" --skip-lock-tables --no-create-info > ttpj_alert.sql    

过滤一些大表：   
mysqldump -h'dbdataapp-test01' -u'test_ttpj' -p'[zhbkSkM7xrA.4' -P5002 test_ttpj_db --skip-lock-tables --ignore-table=test_ttpj_db.ttpj_wait_audit_deal --ignore-table=test_ttpj_db.ttpj_strmodule  --ignore-table=test_ttpj_db.mtdeal --ignore-table=test_ttpj_db.crm_ttpj_status --ignore-table=test_ttpj_db.crm_ttpj_match_hotel  --ignore-table=test_ttpj_db.crm_ttpj_match_food --ignore-table=test_ttpj_db.crm_ttpj_deal_price_change --ignore-table=test_ttpj_db.crm_ttpj_data2 --ignore-table=test_ttpj_db.crm_ttpj_data --ignore-table=test_ttpj_db.compdeal> test_ttpj2.sql    

## 将线上数据库导出到线下数据库    

在线下数据库中导入*.sql文件就可以了。



