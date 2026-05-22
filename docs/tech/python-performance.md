# Python性能优化指南

## 性能分析工具

### cProfile
```python
import cProfile
cProfile.run('your_function()')
```

### line_profiler
```python
from line_profiler import LineProfiler
profiler = LineProfiler(your_function)
profiler.runcall(your_function)
profiler.print_stats()
```

## 优化策略

### 1. 数据结构选择
- 频繁查找: 用 `set` 或 `dict` (O(1)) 代替 `list` (O(n))
- 需要排序: 用 `heapq` 处理Top-K问题
- 频繁首尾操作: 用 `collections.deque`

### 2. 避免全局变量
```python
# 慢: 全局变量查找
global_var = 100
def slow_func():
    return global_var * 2

# 快: 局部变量
def fast_func():
    local_var = 100
    return local_var * 2
```

### 3. 使用生成器
```python
# 慢: 一次性加载
def load_all():
    return [process(item) for item in large_dataset]

# 快: 惰性求值
def load_lazy():
    for item in large_dataset:
        yield process(item)
```

### 4. 字符串拼接
```python
# 慢
result = ""
for s in strings:
    result += s

# 快
result = "".join(strings)
```

### 5. 使用内置函数
- `map()`, `filter()` 比循环快
- `sum()`, `max()`, `min()` 用C实现
- `sorted()` 比手动排序快

---
*更新时间: {DATETIME_STR}*
