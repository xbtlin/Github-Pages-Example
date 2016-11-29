

select * from mart_catering.dim_common_xmd_poi_ss where partition_date='2016-11-01' and partition_chain = 'mt' and (mt_poi_cate3_name is null or mt_poi_cate3_name ='') limit 1000

三级品类为空只有500个左右，可以忽略不计。

mt_main_poi_id
poi用这张表   mart_catering.dim_common_xmd_poi_ss   
三级品类名：mt_poi_cate3_name 
三级品类id: mt_poi_cate3_id
日期分区：partition_date
渠道分区：partition_chain
mt_city_id



城市用这张表   mart_catering.dim_common_xmd_city
partition_date
mt_city_id
is_mt_online
mt_city_rank


高星酒店名单
ba_hotel.dim_hotel_poi
这个表里
is_high_star	string	是否为高星酒店（0=否 1=是）

后台品类之间没有重叠。第i个后台品类poi集合是Ai,则Ai和Aj（i!=j）的交集为0。

select transform(x, y, z....) using 'xxx.py' as (xx, yy, zz....) from .... 

category





  ,case when a.tagsubtype in ('名人投资','名人使用','名人主题','名人母校','名人建造','名人合照','名人故居','名人事件','名人题字') then a.shortintro else 'none' end as famous_others
  ,case when a.tagsubtype='名人开店' then a.shortintro else 'none' end as famous_setup
  ,case when a.tagsubtype='名人推荐' then a.shortintro else 'none' end as famous_recommend
  ,case when a.tagsubtype='影视作品取景地' then a.shortintro else 'none' end as film_place
  ,case when a.tagsubtype='影视作品取景地' then a.shortintro else 'none' end as film_place
  ,case when a.tagsubtype='名人光顾' then a.shortintro else 'none' end as famous_came
  ,case when a.tagsubtype='媒体推荐' and a.tags='点评精选榜单' then a.shortintro else 'none' end as dianping_featured
  ,case when a.tagsubtype='媒体推荐' and (a.tags rlike '(.*?)公众号(.*?)' 
    or a.tags rlike '(.*?)微博(.*?)' or a.tags rlike '(.*?)新浪美食(.*?)' 
    or a.tags rlike '(.*?)马蜂窝(.*?)' or a.tags rlike '(.*?)公众号(.*?)' 
    or a.tags rlike '(.*?)携程(.*?)') then a.shortintro else 'none' end as internet_media
  ,case when a.tagsubtype!='媒体推荐' or a.tags='点评精选榜单'
    or (a.tags rlike '(.*?)公众号(.*?)' 
    or a.tags rlike '(.*?)微博(.*?)' or a.tags rlike '(.*?)新浪美食(.*?)' 
    or a.tags rlike '(.*?)马蜂窝(.*?)' or a.tags rlike '(.*?)公众号(.*?)' 
    or a.tags rlike '(.*?)携程(.*?)') then 'none' else a.shortintro end as tradition_media
    
gr.comment RLIKE '.*(商家营业但不接待|商家停业/装修/转让|商家说可以直接以团购价到店消费).*'
    
    
    
    ,case when a.tagsubtype='媒体推荐' and (a.tags rlike '.*(公众号|微博|新浪美食|马蜂窝|公众号|携程).*') then a.shortintro else 'none' end as internet_media
  ,case when a.tagsubtype!='媒体推荐' and ( a.tags='点评精选榜单'
    or (a.tags rlike '.*(公众号|微博|新浪美食|马蜂窝|公众号|携程).*')) then 'none' else a.shortintro end as tradition_media
    
    
      ,famous_others
      ,famous_setup
      ,famous_recommend
      ,film_place
      ,famous_came
      ,internet_media
      ,tradition_media
      ,dianping_featured
      ,tag_level
    
    
    

            # outlist=[]
            # outlist.append(str(cols[0]))
            # outlist.append(famous_others)
            # outlist.append(famous_setup)
            # outlist.append(famous_recommend)
            # outlist.append(film_place)
            # outlist.append(famous_came)
            # outlist.append(internet_media)
            # outlist.append(tradition_media)
            # outlist.append(dianping_featured)
            # outlist.append(str(tag_level))
            # print "\t".join(outlist)
            
            
            

Error: java.lang.RuntimeException: org.apache.hadoop.hive.ql.metadata.HiveException: Hive Runtime Error while processing row (tag=0) {"key":{"_col0":35654,"_col1":"味千拉面","_col2":"权威推荐","_col3":"媒体推荐","_col4":"点评精选榜单","_col5":"异国风味美食"},"value":null}
	at org.apache.hadoop.hive.ql.exec.mr.ExecReducer.reduce(ExecReducer.java:283)
	at org.apache.hadoop.mapred.ReduceTask.runOldReducer(ReduceTask.java:444)
	at org.apache.hadoop.mapred.ReduceTask.run(ReduceTask.java:392)
	at org.apache.hadoop.mapred.YarnChild$2.run(YarnChild.java:164)
	at java.security.AccessController.doPrivileged(Native Method)
	at javax.security.auth.Subject.doAs(Subject.java:415)
	at org.apache.hadoop.security.UserGroupInformation.doAs(UserGroupInformation.java:1657)
	at org.apache.hadoop.mapred.YarnChild.main(YarnChild.java:158)
Caused by: org.apache.hadoop.hive.ql.metadata.HiveException: Hive Runtime Error while processing row (tag=0) {"key":{"_col0":35654,"_col1":"味千拉面","_col2":"权威推荐","_col3":"媒体推荐","_col4":"点评精选榜单","_col5":"异国风味美食"},"value":null}
	at org.apache.hadoop.hive.ql.exec.mr.ExecReducer.reduce(ExecReducer.java:271)
	... 7 more
Caused by: org.apache.hadoop.hive.ql.metadata.HiveException: [Error 20001]: An error occurred while reading or writing to your custom script. It may have crashed with an error.
	at org.apache.hadoop.hive.ql.exec.ScriptOperator.processOp(ScriptOperator.java:410)
	at org.apache.hadoop.hive.ql.exec.Operator.forward(Operator.java:796)
	at org.apache.hadoop.hive.ql.exec.SelectOperator.processOp(SelectOperator.java:87)
	at org.apache.hadoop.hive.ql.exec.Operator.forward(Operator.java:796)
	at org.apache.hadoop.hive.ql.exec.GroupByOperator.forward(GroupByOperator.java:1064)
	at org.apache.hadoop.hive.ql.exec.GroupByOperator.processAggr(GroupByOperator.java:875)
	at org.apache.hadoop.hive.ql.exec.GroupByOperator.processKey(GroupByOperator.java:737)
	at org.apache.hadoop.hive.ql.exec.GroupByOperator.processOp(GroupByOperator.java:803)
	at org.apache.hadoop.hive.ql.exec.mr.ExecReducer.reduce(ExecReducer.java:262)
	... 7 more







python中dict如何添加元素


elif int(cols[2]) in TYPE2MAP.keys():
                front_cate2_name = TYPE2MAP[int(cols[2])]
            else:
                continue


Error: java.lang.RuntimeException: Hive Runtime Error while closing operators: [Error 20003]: An error occurred when trying to close the Operator running your custom script.
	at org.apache.hadoop.hive.ql.exec.mr.ExecReducer.close(ExecReducer.java:326)
	at org.apache.hadoop.mapred.ReduceTask.runOldReducer(ReduceTask.java:453)
	at org.apache.hadoop.mapred.ReduceTask.run(ReduceTask.java:392)
	at org.apache.hadoop.mapred.YarnChild$2.run(YarnChild.java:164)
	at java.security.AccessController.doPrivileged(Native Method)
	at javax.security.auth.Subject.doAs(Subject.java:415)
	at org.apache.hadoop.security.UserGroupInformation.doAs(UserGroupInformation.java:1657)
	at org.apache.hadoop.mapred.YarnChild.main(YarnChild.java:158)
Caused by: org.apache.hadoop.hive.ql.metadata.HiveException: [Error 20003]: An error occurred when trying to close the Operator running your custom script.
	at org.apache.hadoop.hive.ql.exec.ScriptOperator.close(ScriptOperator.java:514)
	at org.apache.hadoop.hive.ql.exec.Operator.close(Operator.java:591)
	at org.apache.hadoop.hive.ql.exec.Operator.close(Operator.java:591)
	at org.apache.hadoop.hive.ql.exec.mr.ExecReducer.close(ExecReducer.java:318)
	... 7 more


FAILED: Execution Error, return code 20003 from org.apache.hadoop.hive.ql.exec.mr.MapRedTask. An error occurred when trying to close the Operator running your custom script.
MapReduce Jobs Launched: 
Job 0: Map: 285  Reduce: 9   Cumulative CPU: 2675.12 sec   HDFS Read: 458976394 HDFS Write: 0 FAIL
Total MapReduce CPU Time Spent: 44 minutes 35 seconds 120 msec
)
Fail in Action load



Error: java.lang.RuntimeException: org.apache.hadoop.hive.ql.metadata.HiveException: Hive Runtime Error while processing row {"chain":null,"poi_id":null,"xmd_main_poi_id":null,"mt_main_poi_id":104728560,"poi_name":null,"poi_phone":null,"address":null,"barea_id":null,"brand_id":null,"brand_name":null,"poi_close_status":null,"latitude":null,"longitude":null,"nation_code":null,"org_id":null,"org_name":null,"org_rank":null,"org_type":null,"main_org_id":null,"main_org_name":null,"mt_city_id":null,"city_name":null,"mt_main_city_id":null,"main_city_name":null,"mt_province_id":null,"province_name":null,"region_id":null,"region_name":null,"district_id":null,"district_name":null,"state_id":null,"state_name":null,"mt_poi_cate3_id":179,"mt_poi_cate3_name":null,"mt_poi_cate2_id":249,"mt_poi_cate2_name":null,"mt_poi_cate1_id":null,"mt_poi_cate1_name":null,"management_type":null,"partition_date":"2016-11-08","partition_chain":"dp"}
	at org.apache.hadoop.hive.ql.exec.mr.ExecMapper.map(ExecMapper.java:195)
	at org.apache.hadoop.mapred.MapRunner.run(MapRunner.java:54)
	at org.apache.hadoop.mapred.MapTask.runOldMapper(MapTask.java:453)
	at org.apache.hadoop.mapred.MapTask.run(MapTask.java:343)
	at org.apache.hadoop.mapred.YarnChild$2.run(YarnChild.java:164)
	at java.security.AccessController.doPrivileged(Native Method)
	at javax.security.auth.Subject.doAs(Subject.java:415)
	at org.apache.hadoop.security.UserGroupInformation.doAs(UserGroupInformation.java:1657)
	at org.apache.hadoop.mapred.YarnChild.main(YarnChild.java:158)
Caused by: org.apache.hadoop.hive.ql.metadata.HiveException: Hive Runtime Error while processing row {"chain":null,"poi_id":null,"xmd_main_poi_id":null,"mt_main_poi_id":104728560,"poi_name":null,"poi_phone":null,"address":null,"barea_id":null,"brand_id":null,"brand_name":null,"poi_close_status":null,"latitude":null,"longitude":null,"nation_code":null,"org_id":null,"org_name":null,"org_rank":null,"org_type":null,"main_org_id":null,"main_org_name":null,"mt_city_id":null,"city_name":null,"mt_main_city_id":null,"main_city_name":null,"mt_province_id":null,"province_name":null,"region_id":null,"region_name":null,"district_id":null,"district_name":null,"state_id":null,"state_name":null,"mt_poi_cate3_id":179,"mt_poi_cate3_name":null,"mt_poi_cate2_id":249,"mt_poi_cate2_name":null,"mt_poi_cate1_id":null,"mt_poi_cate1_name":null,"management_type":null,"partition_date":"2016-11-08","partition_chain":"dp"}
	at org.apache.hadoop.hive.ql.exec.MapOperator.process(MapOperator.java:550)
	at org.apache.hadoop.hive.ql.exec.mr.ExecMapper.map(ExecMapper.java:177)
	... 8 more
Caused by: org.apache.hadoop.hive.ql.metadata.HiveException: [Error 20001]: An error occurred while reading or writing to your custom script. It may have crashed with an error.
	at org.apache.hadoop.hive.ql.exec.ScriptOperator.processOp(ScriptOperator.java:410)
	at org.apache.hadoop.hive.ql.exec.Operator.forward(Operator.java:796)
	at org.apache.hadoop.hive.ql.exec.SelectOperator.processOp(SelectOperator.java:87)
	at org.apache.hadoop.hive.ql.exec.Operator.forward(Operator.java:796)
	at org.apache.hadoop.hive.ql.exec.TableScanOperator.processOp(TableScanOperator.java:92)
	at org.apache.hadoop.hive.ql.exec.Operator.forward(Operator.java:796)
	at org.apache.hadoop.hive.ql.exec.MapOperator.process(MapOperator.java:540)
	... 9 more
Caused by: java.io.IOException: Stream closed
	at java.lang.ProcessBuilder$NullOutputStream.write(ProcessBuilder.java:434)
	at java.io.OutputStream.write(OutputStream.java:116)
	at java.io.BufferedOutputStream.flushBuffer(BufferedOutputStream.java:82)
	at java.io.BufferedOutputStream.write(BufferedOutputStream.java:121)
	at java.io.BufferedOutputStream.flushBuffer(BufferedOutputStream.java:82)
	at java.io.BufferedOutputStream.write(BufferedOutputStream.java:95)
	at java.io.DataOutputStream.write(DataOutputStream.java:88)
	at org.apache.hadoop.hive.ql.exec.TextRecordWriter.write(TextRecordWriter.java:54)
	at org.apache.hadoop.hive.ql.exec.ScriptOperator.processOp(ScriptOperator.java:378)
	... 15 more


FAILED: Execution Error, return code 20001 from org.apache.hadoop.hive.ql.exec.mr.MapRedTask. An error occurred while reading or writing to your custom script. It may have crashed with an error.