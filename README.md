## Copy contents of one table into another (column names and types must be the same)
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
