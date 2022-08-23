---
title: 用命令激活office2010
date: 2022-08-23 15:02:25
tags:
 - office
 - 电脑操作技巧
---

32位系统装32位office或者64位系统装64位office命令：
```bash
cd "C:\Program Files\Microsoft Office\Office14"
```
64位系统装32位office命令：
```bash
cd "C:\Program Files (x86)\Microsoft Office\Office14"
```
然后执行如下命令：
```bash
cscript ospp.vbs /inpkey:VYBBJ-TRJPB-QFQRF-QFT4D-H3GVB
cscript ospp.vbs /sethst:kms.03k.org
cscript ospp.vbs /act
cscript ospp.vbs /dstatus
```
最后看到命令行这里显示 LICENSE STATUS :--- LICENSED---  (表示永久授权)
