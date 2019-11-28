# POSTGRES

## 1. 查询表名称
```
# psql
\dt

# SQL
select tablename from pg_tables;
```
----

## 2. 查询表结构
```
# psql
\d {{表名}}

# SQL
SELECT
	a.attnum,
	a.attname AS field,
	t.typname AS type,
	a.attlen AS length,
	a.atttypmod AS lengthvar,
	a.attnotnull AS notnull,
	b.description AS COMMENT 
FROM
	pg_class c,
	pg_attribute a
	LEFT OUTER JOIN pg_description b ON a.attrelid = b.objoid 
	AND a.attnum = b.objsubid,
	pg_type t 
WHERE
	c.relname = '{{表名}}' 
	AND a.attnum > 0 
	AND a.attrelid = c.oid 
	AND a.atttypid = t.oid 
ORDER BY
	a.attnum;
```
----

## 3. 美化输出
mysql中，select * from table\g;  
在postgres的psql中，\x的作用大致相同
```
postgres=# \x
Expanded display is off.
postgres=# \x
Expanded display is on.
```
----

## 3. 列函数
https://www.postgresql.org/docs/9.2/functions-array.html  
unnset
```

SELECT
	id,
	NAME,
	email,
	unnest ( ARRAY [ groups ] ) AS g_id,
	details -> 'active_at' AS active_at,
	created_at 
FROM
	users

```
----

## 4. 取出json中的值

```

# 取出json列中的某个数据
select id, details->'active_at' as active_at from users limit 10

```
