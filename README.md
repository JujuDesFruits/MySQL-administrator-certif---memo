# MySQL Database Administrator - certif

### Rebuilt and repair

1. rebuild table by dumping and reloading it
```
mysqldump *db_name* *t1* > dump.sql
mysql *db_name* < dump.sql
```
2. rebuild all tables in a single Database
```
mysqldump *db_name* > dump.sql
mysql *db_name* < dump.sql
```
3. rebuild all tables in all Database
```
mysqldump --all-databases > dump.sql
mysql *db_name* < dump.sql
```

### Copying databases
```
mkdir *DUMPDIR*
mysqldump --tab=*DUMPDIR* *db_name*
```
