---
title: 升级bash
date: 2022-08-23 17:24:19
tags:
- linux
- bash
- 安全加固
- 源码编译
---

*不要以为很难，其实很简单，也不危险。*

1. 下载个对应版本的 texinfo
```bash
wget https://mirrors.163.com/centos-vault/4.5/os/x86_64/CentOS/rpm/texinfo-4.7-5.el4.2.x86_64.rpm
```
2. 下载 bash 的最新版本源码文件
```bash
wget https://mirrors.tuna.tsinghua.edu.cn/gnu/bash/bash-5.2-rc2.tar.gz
```
3. 检查当前版本
```bash
bash --version
cat /etc/redhat-release
uname -a
```
4. 解压、编译、安装三步：
```bash
cp /home/xxx/bash-5.2-rc2.tar.gz /usr/local
cd /usr/local
tar -zxf  bash-5.2-rc2.tar.gz
cd bash-5.2-rc2
./configure
make
make install
mv /bin/bash /bin/bash.bak
ln -s /usr/local/bash-5.2-rc2/bash /bin/bash
```
5. 检查版本
```bash
bash --version
```
