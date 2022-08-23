---
title: IHS+Plugin+WAS SSL单向认证
date: 2022-08-22 17:55:19
tags:
  - IBM
  - SSL
  - IHS
  - apache
  - ikeyman
---
h1. 启用SLL功能
1. 创建IHS自签名证书
打开ikeyman工具
```bash
cd /opt/IBM/HTTPServer/bin
./ikeyman.#!/bin/sh
```
*新建密钥数据库*
存储位置设置为 /opt/IBM/HTTPServer/，文件名为ihsserverkey.kdb，并确定。  
在弹出窗口中：
  输入密码：
  选中“将密码存储到文件”选项。
  点击“确定”按钮。
*新建自签名证书*
在“新建自签名证书”的窗口  

|属性名|值|
|------|---|
|密钥标签|ihsserverkey|
|版本|X509 V3|
|密钥大小|2048位|
|签名算法|默认|
|共用名|默认|
|有效期|3650天|

2. 修改 /opt/IBM/HTTPServer/conf/httpd.conf 文件  
```bash
LoadModule ibm\_ssl\_module modules/mod/_ibm/_ssl.so
Listen 0.0.0.0:443

Listen [::]:443
<VirtualHost *:443>
  SSLEnable
  SSLProtocolDisable SSLv2
  SSLClientAuth none
</VirtualHost>
KeyFile /opt/IBM/HTTPServer/ihsserverkey.kdb
SSLDisable

```
3. 更新Web插件
打开was控制台http://localhost:9060/admin  
  切换到“系统环境”，“更新Web插件”，点击“更新”；  
  切换到“服务器管理”，“web服务器”；  
  选中“webserver1”  
    点击“生成插件”；
    再点击“传播插件”；
    重启IIS。
