# functools工具集

## lru_cache
```python
from functools import lru_cache

@lru_cache(maxsize=128)
def fibonacci(n):
    if n < 2: return n
    return fibonacci(n-1) + fibonacci(n-2)
```

## partial
```python
from functools import partial
double = partial(pow, exp=2)
```

## singledispatch
```python
from functools import singledispatch

@singledispatch
def process(arg):
    raise TypeError

@process.register(int)
def _(arg):
    return arg * 2
```

## wraps
```python
from functools import wraps
def my_decorator(func):
    @wraps(func)
    def wrapper(*args, **kwargs):
        return func(*args, **kwargs)
    return wrapper
```
