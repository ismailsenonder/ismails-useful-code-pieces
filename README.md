## (MSSQL) Search text in procedures, triggers and functions.

#### Method 1
```sql
SELECT DISTINCT o.name AS Object_Name, o.type_desc FROM sys.sql_modules m 
INNER JOIN sys.objects o ON m.object_id = o.object_id WHERE m.definition Like ‘%search_text%’;  
```
#### Method 2
```sql
SELECT name FROM sys.procedures WHERE Object_definition(object_id) LIKE ‘%search_text%’  
```

## (MSSQL) Copy contents of one table into another
Noe: Column names and types must be the same
#### Copy all records
```sql
SELECT * INTO new_table FROM old_table;  
```
#### Copy all records from a table that belongs to another database
```sql
SELECT * INTO new_table IN 'newdb.mdb' FROM old_table;  
```
#### Copy selected columns only
```sql
SELECT column_name1, column_name2 INTO new_table FROM old_table;
```
#### Copy specified number of records
```sql
SELECT TOP 100 * INTO new_table FROM old_table;
```

## (MSSQL) Get all tables containing columns with a specified name
```sql
SELECT c.name AS ColName, t.name AS TableName
FROM sys.columns c
JOIN sys.tables t ON c.object_id = t.object_id
WHERE c.name LIKE '%colName%';
```

## (MSSQL) Get all table names in a database
```sql
SELECT TABLE_NAME
FROM INFORMATION_SCHEMA.TABLES
WHERE TABLE_TYPE = 'BASE TABLE' AND TABLE_CATALOG='dbName'
```

## (MySQL) Get all table names in a database
```sql
SELECT TABLE_NAME 
FROM INFORMATION_SCHEMA.TABLES
WHERE TABLE_TYPE = 'BASE TABLE' AND TABLE_SCHEMA='dbName' 
```

## (MySQL) Find all procedures and functions that uses, references or depends on a table
```sql
SELECT * FROM Mysql.proc where body LIKE '%table_name%';
```

