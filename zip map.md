# zip
```

zip(seq1 [, seq2 [...]]) -> [(seq1[0], seq2[0] ...), (...)]

Return a list of tuples, where each tuple contains the i-th element
from each of the argument sequences.  The returned list is truncated
in length to the length of the shortest argument sequence.
Type:      builtin_function_or_method
```
```
In [42]: zip([1, 2], ['a', 'b'], ('ooo', 'ppp'))
Out[42]: [(1, 'a', 'ooo'), (2, 'b', 'ppp')]
```

# map

将 function 应用到每个元素中
```
In [43]: map?
Docstring:
map(function, sequence[, sequence, ...]) -> list

Return a list of the results of applying the function to the items of
the argument sequence(s).  If more than one sequence is given, the
function is called with an argument list consisting of the corresponding
item of each sequence, substituting None for missing values when not all
sequences have the same length.  If the function is None, return a list of
the items of the sequence (or a list of tuples if more than one sequence).
Type:      builtin_function_or_method
```

```
In [44]: map(lambda x: x +1, [1, 2, 3])
Out[44]: [2, 3, 4]
```

# dict
```
In [46]: dict?
Docstring:
dict() -> new empty dictionary
dict(mapping) -> new dictionary initialized from a mapping object's
    (key, value) pairs
dict(iterable) -> new dictionary initialized as if via:
    d = {}
    for k, v in iterable:
        d[k] = v
dict(**kwargs) -> new dictionary initialized with the name=value pairs
    in the keyword argument list.  For example:  dict(one=1, two=2)
Type:      type
```

```
In [47]: l = [(1, 2), ('ooo', 'ppp'), (6666, 6666)]

In [48]: dict(l)
Out[48]: {1: 2, 6666: 6666, 'ooo': 'ppp'}
```