# MySQL Table的空间占用


## 1.粗略统计
``` SQL

SELECT
	CONCAT( table_schema, '.', table_name ) AS 'Table Name',
	table_rows AS 'Number of Rows',
	CONCAT( ROUND( data_length / ( 1024 * 1024 * 1024 ), 6 ), ' G' ) AS 'Data Size',
	CONCAT( ROUND( index_length / ( 1024 * 1024 * 1024 ), 6 ), ' G' ) AS 'Index Size',
	CONCAT( ROUND( ( data_length + index_length ) / ( 1024 * 1024 * 1024 ), 6 ), ' G' ) AS 'Total' 
FROM
	information_schema.TABLES 
WHERE
	table_schema LIKE 'redash';

```
----

## 2.InnoDB表重建recreate
delete操作会将主树上的数据作删除标记，but空间不回收，备之后复用
update操作可能会产生页分裂  
insert在中间id操作可能产生页分裂   

``` SQL

# InnoDB重建表，回收这部分空间
alter table {{table_name}} engine = innodb, algorithm=inplace, lock=none;
# optimize == recreate  + analyze

```
---- 

## 3. 重建之后可能表会变大：

在重建表的时候，InnoDB 不会把整张表占满，每个页留了 1/16 给后续的更新用。  
也就是说，其实重建表之后不是“最”紧凑的。
