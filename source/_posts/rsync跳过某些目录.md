---
title: rsync跳过某些目录
date: 2022-08-23 15:17:17
tags:
- 实施技巧
- linux
- rsync
---
说明：
  1. 使用 --exclude 参数，可以有多个  
  2. exclude 后面跟的是要过滤的文件或文件夹名称，可以用正则表达式
  3. exclude 参数必须放在“源文件夹”的前面

```bash
 rsync -aux --exclude "appbak" /源文件夹/* /目标文件夹/
```
