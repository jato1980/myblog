---
title: h5版OA如何定位service对应的类
date: 2022-08-23 14:48:15
tags:
 - 京华OA系统(H5版)
 - 京华信息科技股份有限公司
 - 实施技巧
 - java
 - xml
 - war
 - jar
---

假设URL中的地址为：
```java
/newoa/services?&SERVICE=OA.ScheduleService.queryLeaderSchedule
```
*如何查找如上url中的ScheduleService对应的是哪一个类文件呢？*

操作方法如下：  
  1. 首先，用压缩工具打开serviceWeb.war，进入lib文件夹，找到service-xx.jar包；   
  2. 将service-xx.jar解压到本地，用压缩工具打开，查看applicationContext-xx.xml，其中的xx为模块名称。  
>例如本例中为 workrelate ，jar 文件名为：service-workrelate.jar , 配置文件名称为 applicationContext-workrelate.xml

  3. 找到如下内容：
```xml
<bean id="scheduleService" class="com.excellence.work.tswk.service.impl.ScheduleServiceImpl">
```
>其中class对应的内容就是这个服务对类的类名和路径。  
queryLeaderSchedule 这个是这个类里的其中一个方法：
```java
public JSONObject queryLeaderSchedule(ServiceRequest request, String leaderStruts)
```
