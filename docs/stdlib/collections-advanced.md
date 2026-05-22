# collections高级容器

## defaultdict
```python
from collections import defaultdict
d = defaultdict(list)
d['key'].append('value')
```

## Counter
```python
from collections import Counter
c = Counter('abracadabra')
print(c.most_common(3))
```

## deque
```python
from collections import deque
q = deque(maxlen=10)
q.append(1)
q.appendleft(0)
```

## namedtuple
```python
from collections import namedtuple
Point = namedtuple('Point', ['x', 'y'])
p = Point(1, 2)
```

## ChainMap
```python
from collections import ChainMap
combined = ChainMap(dict1, dict2)
```
