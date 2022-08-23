---
title: 编译升级apache2.4.53
date: 2022-08-22 18:47:17
tags:
 - apache
 - 编译
 - gcc
 - make
 - 源文件
 - linux
---

*编译环境准备*
```bash
yum -y install gcc make pcre-devel openssl-devel expat-devel
```

*下载相关源文件*
```bash
cd /usr/local/
wget https://dlcdn.apache.org/httpd/httpd-2.4.53.tar.gz
wget http://archive.apache.org/dist/apr/apr-util-1.6.1.tar.gz
wget http://archive.apache.org/dist/apr/apr-1.7.0.tar.gz
```

*解压*
```bash
tar -xf httpd-2.4.53.tar.gz
tar -xf apr-1.7.0.tar.gz -C httpd-2.4.53/srclib
tar -xf apr-util-1.6.1.tar.gz -C httpd-2.4.53/srclib
cd httpd-2.4.53/srclib
mv apr-1.7.0 apr
mv apr-util-1.6.1 apr-util
cd ../
```

*配置*
```bash
./configure --prefix=/usr/local/apache24 --enable-so --enable-ssl --enable-rewrite \
 --with-zlib --with-pcre --with-included-apr --with-included-apr-util \
 --enable-modules=most --enable-mpms-shared=all --with-mpm=prefork
```
>说明：  
  --prefix 安装位置

*编译*
```bash
make
```
*安装*
```bash
make install
```
