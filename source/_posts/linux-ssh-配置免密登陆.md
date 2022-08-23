---
title: linux 两步配置ssh免密登陆
date: 2022-08-23 15:37:33
tags:
- ssh
- 公钥
- rsync
- 备份
- 实施技巧
---

*1. 生成公钥*
```bash
ssh-keygen
```
>执行完成后，会在主目录下生成.ssh/id_rsa.pub

*2. 将公钥发送到ssh服务器*
```bash
ssh-copy-id -i ~/.ssh/id_rsa.pub root@x.x.x.x
```
>说明：  
x.x.x.x 为目标服务器IP地址


成功配置好后rsync做备份就不会再要求输入密码了。
```bash
rsync -avzu --progress root@x.x.x.x:/源文件夹/* /目标文件夹/
```
