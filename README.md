# MySQL Database Administrator - certif
To help me manipulating an  MYSQL database, I use a script made by myself in an old project:
```
./create_Database.sh
```
Queries can be found as axample in "queries.txt"

## Rebuilt and repair

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

## Copying databases
creating repository
```
mkdir DUMPDIR
mysqldump --tab=DUMPDIR *db_name*
```
create db, import table, import data
```
mysqladmin create *db_name*
cat DUMPDIR/*.sql | mysql *db_name*
mysqlimport *db_name* DUMPDIR/*.txt
```

## Queries
- SHOW
- DESCRIBE
- CREATE
- INSERT INTO 

* SELECT
* FROM
* WHERE
* 

## Load data
```
LOAD DATA LOCAL INFILE '*/path/data.txt*' INTO TABLE *t1*
```
