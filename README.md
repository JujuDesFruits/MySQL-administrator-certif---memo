# MySQL Database Administrator - certif
To help me manipulating an  MYSQL database, I use a script made by myself in an old project:
```
./create_Database.sh
```
Queries can be found as axample in "queries.txt"

## Basics elements
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

### Queries
- SHOW [documentation](https://dev.mysql.com/doc/refman/8.0/en/show.html)
- DESCRIBE [documentation](https://dev.mysql.com/doc/refman/8.0/en/describe.html)
- CREATE [documentation](https://dev.mysql.com/doc/refman/8.0/en/create-table.html)
- DELETE [documentation](https://dev.mysql.com/doc/refman/8.0/en/delete.html)
- UPDATE [documentation](https://dev.mysql.com/doc/refman/5.5/en/update.html)
- INSERT [documentation](https://dev.mysql.com/doc/refman/8.0/en/insert.html)

```
SELECT (DISTINCT/COUNT/MAX), (*another querie*) AS *result*
FROM
JOIN ON
WHERE (AND/OR/LIKE)
ORDER BY (DESC/ASC)
GROUP BY
LIMIT
```

### Load data
```
LOAD DATA LOCAL INFILE '*/path/data.txt*' INTO TABLE *t1*
```

### Pattern Matching
t%=thanks/this and %t=bot/commit
(\_)could be any character size one
[abc]=match a, or b or c
[a-z]=match any letter [0-9]=any digit
```
SELECT * FROM *t1* WHERE REGEXP_LIKE(*t1*, '[abc]')
```

### In shell mode
to lunch file containing command in bash, just type
```
mysql < batch-file
```

### User-defined Variable
in this example, we save two value, @min_price, @max_price
```
mysql> SELECT @min_price:=MIN(price),@max_price:=MAX(price) FROM shop;
mysql> SELECT * FROM shop WHERE price=@min_price OR price=@max_price;
```

## MySQL Program
- **mysqld**
  the SQL daemon
- **mysqld_multi**
  server startup script, start and stop multiple servers
- **comp_err**
  compiles error message files froml the error source files
- **mysql_secure_installation**
  improve the security
- **mysql_ssl_rsa_setup**
  create ssl certifcate and key files and RSA key-pair files
- **mysql_tzinfo_to_sql**
  init time zone info
- **mysql_upgrade**
  check tables for incompatibilities
- **mysql**
  command line tool
- **mysqladmin**
  client preforming administrative operation
- **mysqlcheck**
  checks, repairs, analyzes, and optimizes tables
- **mysqldump**
  save databases
- **mysqlimport**
  import text file as data
- **mysqlpump**
  dumps a MySQL database into a file as SQL

see more at this [link](https://dev.mysql.com/doc/refman/8.0/en/programs-overview.html)
