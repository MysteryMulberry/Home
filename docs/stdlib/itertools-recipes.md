# itertools实用配方

## 排列组合
```python
from itertools import permutations, combinations, product
list(permutations('ABC', 2))
list(combinations(range(4), 2))
list(product('AB', '12'))
```

## 无限迭代器
```python
from itertools import count, cycle, repeat
for i in count(10, 2):  # 10, 12, 14, ...
    if i > 20: break
```

## 分组与筛选
```python
from itertools import groupby, filterfalse
for key, group in groupby(sorted(items, key=fn), key=fn):
    print(key, list(group))
```

## 链式操作
```python
from itertools import chain, islice, starmap
flat = chain.from_iterable(nested_lists)
first_10 = islice(infinite_iter, 10)
```
