# ================ Mysql ================

Detail: [Mysql doc](https://www.w3schools.com/sql/)

- For login mysql DB.

```
mysql -u root -p
```

- Create database.

```sql
create database [DBname];
```

- Show all the databases.

```sql
show databases;
```

- Select a DB and enter in.

```
use [DBname];
```

- Show all the tables in this DB.

```sql
show tables;
```

- Show this table data structure.

```sql
describe [tableName];
```

- Query the data from table.

```sql
SELECT [columnA], [columnB] FROM [tableName];
```

- Add new data rows into table.

```sql
INSERT INTO [tableName] (column_1, column_2, column_3)
VALUES (1000, 'Eddie', '19111021');
```

- Update the table data.

```sql
UPDATE [tableName] SET [columnA]='123' WHERE [columnB]='ABC';
```

- Update data if exist otherwise insert new data.  
  `INSERT ON DUPLICATE KEY UPDATE`

```sql
INSERT INTO [tableName] (column_1, column_2, column_3, ...)
VALUES (value_1, value_2, value_3, ...)
ON DUPLICATE KEY UPDATE
  column_1 = VALUES(column_1), column_2 = VALUES(column_2), ...;
```

- Drop database.

```sql
drop database [DatabaseName];
```

- Delete table rows.

```sql
DELETE FROM [table_name] WHERE [some_column] = 'testFail';
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

```sql
create index [index_name] on [table_name] (column1, column2, ...);
```

- Creates a **PRIMARY KEY** on the "ID" column when the "Persons" table is created

```sql
CREATE TABLE [tableName] (
  ID int NOT NULL,
  [AAA] varchar(255) NOT NULL,
  [BBB] varchar(255),
  [CCC] int,
  PRIMARY KEY (ID)
);
```

- Diagnose the query process.

```sql
explain select [column1] from [tableName];
```

# =============== PostgreSQL ===============

Detail: [PostgreSQL doc](https://www.postgresqltutorial.com/)

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

```sql
DROP DATABASE [database_name] WITH (FORCE);
```

# =========== Oracle Database ===========

Detail: [Oracle doc](https://docs.oracle.com/en/database/oracle/sql-developer-web/sdwad/object-navigator-and-files.html#GUID-88D1B5D3-88A7-4269-BE7A-C286B1E663DE)

PS: Oracle Database originally support **SQL** buy no **HQL** (**Hibernate** - Java ORM framework).

- Update data if exist otherwise insert new data.  
  `MERGE INTO`

```sql
MERGE INTO [tableName] target
USING (SELECT ? AS Column1, ? AS Column2 FROM dual) source  -- 'USING' is a clause in SQL
ON (target.UniqueColumn = source.Column1) -- Specifies the columns used for matching
WHEN MATCHED THEN
    UPDATE SET target.Column2 = source.Column2 -- If a match is found, perform an update
WHEN NOT MATCHED THEN
    INSERT (Column1, Column2) VALUES (source.Column1, source.Column2); -- If no match is found, perform an insert
```
