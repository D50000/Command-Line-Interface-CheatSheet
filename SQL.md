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
show databases;
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
describe [tableName];
```

- Select the data from table.
```
SELECT [columnA], [columnB] FROM [tableName];
```

- Update the table data.
```
UPDATE [tableName] SET [columnA]='123' WHERE [columnB]='ABC';
```

- Drop database.
```
drop database [DatabaseName];
```

- Export / Import DB
```
mysqldump -u root -p –databases [DBname] > [backupfile.sql]
mysql -u root -p [DBname] < [backupfile.sql]
```

- Logout the mysql.
```
exit
```

- Creates an **index** on a table. (Duplicate values are allowed)
```
create index [index_name] on [table_name] (column1, column2, ...);
```

- Creates a **PRIMARY KEY** on the "ID" column when the "Persons" table is created
```
CREATE TABLE [tableName] (
  ID int NOT NULL,
  [AAA] varchar(255) NOT NULL,
  [BBB] varchar(255),
  [CCC] int,
  PRIMARY KEY (ID)
);
```

- Diagnose the query process.
```
explain select [column1] from [tableName];
```

# ===============   PostgreSQL   ===============
https://www.postgresqltutorial.com/

- Version check.
```
postgres --version
```

- Initiate the database.
```
service [postgresql-version] initdb
```

- Login postgres.
```
sudo -u [username] psql
```

- End of postgresql command.
```
Ctrl + D
```

- Shows all databases
```
\l
\l+   # for more information
```

- Select a DB and enter in.
```
\c [database_name]
```

- Shows all "relations/tables/sequence" schema.
```
\d
\dt
\ds
```

- Drop database.
```
DROP DATABASE [database_name] WITH (FORCE);
```

# ===============   Oracle Database   ===============
