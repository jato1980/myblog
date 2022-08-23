---
title: openssl+apache 源码编译
date: 2022-08-23 14:39:49
tags:
 - openssl
 - apache
 - libtool
 - linux
 - make
 - 编译
 - 源代码
---
*安装说明*  
  需要 libtool, zlib, apr, apr-util, openssl, httpd-2.4.x

>如果libtool没有装，就执行这个安装  
```bash
yum install libtool
```

*编译安装 apr*
```bash
cd apr-1.x.x
./config.nice
make & make install
```
>根据提示执行如下命令：  
```bash
libtool fininsh xxx
```

*编译安装 apr-util*
```bash
cd apr-util-1.x.x
./config.nice
make & make install
```
>根据提示执行  
```bash
libtool fininsh xxx
```

*编译安装 openssl*
```bash
cd openssl-1.1.1q
./configure shared zlib
make
make install
```

*编译安装 apache*
```bash
cd httpd-2.4.x
./configure --prefix=/usr/local/apache24 --enable-so --enable-ssl --enable-rewrite \
 --with-zlib --with-pcre --with-included-apr --with-included-apr-util \
 --enable-modules=most --enable-mpms-shared=all --with-mpm=prefork
make & make install
```

*检查版本*
```bash
/usr/local/apache24/bin/httpd -V
```
