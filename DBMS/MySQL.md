# MySQL

## Triggers

How to detect triggers:

```sql
SELECT CONCAT('Drop trigger ',trigger_name,';') 
FROM information_schema.triggers 
WHERE trigger_schema='base_de_datos';
```

How to delete triggers:

```sql
SELECT CONCAT('Drop trigger ',trigger_name,';') 
FROM information_schema.triggers 
WHERE trigger_schema=BD;
```

## Collation

List of collations [v8.0](https://dev.mysql.com/doc/refman/8.0/en/charset-mysql.html)

How to change collation:

```sql
SELECT CONCAT('ALTER TABLE ',table_name,' CONVERT TO CHARACTER SET latin1 COLLATE latin1_swedish_ci;') FROM TABLES WHERE TABLE_COLLATION='utf8_general_ci' AND TABLE_SCHEMA='YourDatabase';
```

## Engine maintenance

### Space

Get free space value per database:

```sql
SELECT table_schema "database_name", SUM( data_length + index_length ) / 1024 /1024 /1024 "Data Base Size in GB",SUM( data_free )/ 1024 / 1024 /1024 "Free Space in GB"  FROM information_schema.TABLES GROUP BY table_schema ;
```

Get free space value per table in one database:

```sql
SELECT table_schema AS "YourDatabase",
ROUND(SUM(data_length + index_length) / 1024 / 1024 / 1024, 2) AS "Tamaño (GB)"
FROM information_schema.TABLES
GROUP BY table_schema;
```

## Dates

To allow dates with 0000:

```sql
SET SQL_MODE='ALLOW_INVALID_DATES';
```

## Registers per tables

```sql
select table_name,table_rows from information_schema.tables where table_schema='x';
```
