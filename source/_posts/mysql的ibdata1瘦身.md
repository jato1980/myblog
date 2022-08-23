---
title: mysql的ibdata1瘦身
date: 2022-08-23 16:00:56
tags:
- mysql
- 软件优化
- 数据库
- 日常运维
---
1. 统计库里的每个表的记录数
```sql
use information_schema;
select table_name,table_rows from tables where TABLE_SCHEMA = 'masp' order by table_rows desc;
```
2. 备份所有库数据
```bash
mysqldump -uroot -p --skip-lock-tables --all-databases > all_databases.sql
```
3. 清理日志再备份无日志的库数据【可选】
```sql
mysql -uroot -p
use masp
truncate masp_invoker_log;
exit
mysql -uroot -p masp > masp_nolog.sql
```

4. 停止```mysql```服务  
```bash
service mysql stop
```
5. 删除文件
```bash
rm -f ibdata1
rm -f ib_logfile0
rm -f ib_logfile1
```
6.  启动mysql服务
```bash
service mysql start
```
7. 恢复数据
```bash
mysql -uroot -p
use masp
source all_databases.sql
```

说明：  
  1) 如果不做第四步，查询表时会提示表不存在，用```show tables``` 有显示所有表。 关键要保证第二步的备份成功和完整。  
  2) 删除```ibdata1```并启动```mysql```后，会自动生成新的```ibdata1```文件。  
  3) 如果胆小，第三步可以只是把文件改名：
```bash
mv ibdata1 ibdata1_bak
mv ib_logfile0 ib_logfile0_bak
mv ib_logfile1 ib_logfile1_bak
```
  4) 如果忘记```root```的密码，修改 ```my.cnf``` ，在[mysqld]下增加```skip-grant-tables ```
然后重启```mysqld```服务器，再更新```root```的密码：  
```sql
use mysql
update user set password=password('root1234') where user='root' and host = 'localhost';
commit;
```
然后注释```my.cnf```前面加的内容，重启```mysql```。
