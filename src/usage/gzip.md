# gzip

举例：

```bash
# mysqldump --host=xxx.mysql.rds.aliyuncs.com --port=port --user=root --password=your_password --default-character-set=utf8 dbname | gzip > aliyun_rds_xxx_mysql_dump.sql.gz
# ll
total 92
-rw-r--r-- 1 root root 91692 Apr 26 10:56 aliyun_rds_xxx_mysql_dump.sql.gz
```
