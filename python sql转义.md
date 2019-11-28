# python sql转义

## 1. raw字符串

### 报错：把%Y格式化当成字符串的转义
```

sql = """ select date_format(now(), '%Y-%m') """
cursor.execute(sql) 

```

### 正确：需转义 %
```

sql = """ select date_format(now(), '%%Y-%%m') """
cursor.execute(sql) 

```