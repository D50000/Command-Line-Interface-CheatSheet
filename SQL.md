# ================  Mysql  ================
Detail:  
https://www.w3schools.com/sql/

- For login mysql DB.
```
mysql -u root -p
```

- Create database.
```
create database [DBname];
```

- Show all the databases.
```
SHOW DATABASES;
```

- Select a DB and enter in.
```
use [DBname];
```

- Show all the tables in this DB.
```
show tables;
```

- Show this table data structure.
```
describe [tabeName];
```

- Drop database.
```
drop database [DatabaseName];
```

- Export / Import DB
```
mysqldump -u root -p –databases [DBname] > [backupfile.sql]
mysql -u root -p [kms] < [file.sql]
```

- Logout the mysql.
```
exit
```

# ===============   PostgreSQL   ===============
https://www.postgresqltutorial.com/

- Version check
$postgres --version


# ===============   Oracle Database   ===============
