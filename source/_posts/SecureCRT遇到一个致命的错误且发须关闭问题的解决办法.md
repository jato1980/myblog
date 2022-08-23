---
title: SecureCRT遇到一个致命的错误且发须关闭问题的解决办法
date: 2022-08-23 17:50:52
tags:
- windows
- 注册表
- SecureCRT
- 软件错误
- 软件修复
---
regedit 打开注册表
删除以下路径下的 ```VanDyke``` 项
```
   HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node
   HKEY_CURR_USER\SOFTWARE
   HKEY_LOCAL_MACHINE\SOFTWARE\
```
