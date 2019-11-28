# itertools

# 1. itertools.groupby 

**需要先排好序**
## 介绍
```
In [8]: groupby?
Docstring:
groupby(iterable[, keyfunc]) -> create an iterator which returns
(key, sub-iterator) grouped by each value of key(value).
File:      ~/venv/venvpy2/lib/python2.7/lib-dynload/itertools.so
Type:      type
```

## 实操
**需要先排好序**
```
In [2]: a
Out[2]: [(1, 1), (1, 2), (2, 2), (1, 1)]

# 未排序
In [6]: for v0, v in groupby(a, key=lambda x: x[0]):
   ...:     print v0, list(v)
   ...:
1 [(1, 1), (1, 2)]
2 [(2, 2)]
1 [(1, 1)]

# 排好序
In [7]: for v0, v in groupby(sorted(a, key=lambda x: x[0]), key=lambda x: x[0]):
   ...:     print v0, list(v)
   ...:
1 [(1, 1), (1, 2), (1, 1)]
2 [(2, 2)]

```
