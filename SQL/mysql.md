## SQL Queries For Practice or Easier
### get tuple names of a table
```sql
SELECT COLUMN_NAME
FROM INFORMATION_SCHEMA.COLUMNS
WHERE TABLE_SCHEMA = 'your_database_name'
  AND TABLE_NAME = 'your_table_name';
```
