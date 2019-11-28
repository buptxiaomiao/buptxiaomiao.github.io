# HIVE DDL

HIVE DDL DOC: https://cwiki.apache.org/confluence/display/Hive/LanguageManual+DDL
# 表改名
```
alter table old_table_name rename to new_table_name;  
```
----

# 加字段
```
alter table table_name add columns(column_name datatype);

# 示例：
alter table rec_show add columns(page int);

```
----


# 修改字段
```
alter table table_name change column_name new_column_name data_type;

# 示例：
alter table rec_show change page page_id string;
```
----

# 替换列 replace_column
```
alter table employee_data replace columns( id string, first_name string, age int);  
```
