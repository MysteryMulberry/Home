# 迭代器与生成器深入

## 自定义迭代器
```python
class Fibonacci:
    def __init__(self, max_count):
        self.max_count = max_count
        self.a, self.b = 0, 1
        self.count = 0

    def __iter__(self):
        return self

    def __next__(self):
        if self.count >= self.max_count:
            raise StopIteration
        value = self.a
        self.a, self.b = self.b, self.a + self.b
        self.count += 1
        return value
```

## 生成器表达式 vs 列表推导
```python
# 内存友好: 生成器
total = sum(x**2 for x in range(1000000))

# 立即求值: 列表推导
squares = [x**2 for x in range(100)]
```

## yield from
```python
def flatten(nested):
    for item in nested:
        if isinstance(item, list):
            yield from flatten(item)
        else:
            yield item
```

## 异步生成器
```python
async def async_stream():
    for i in range(10):
        await asyncio.sleep(0.1)
        yield i
```

---
*更新时间: {DATETIME_STR}*
