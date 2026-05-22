# 海象运算符 (Walrus Operator) 详解

## 基本语法
```python
if (n := len(data)) > 10:
    print(f"数据量过大: {n} 条")
```

## 常用场景

### while循环
```python
while (line := input()) != "quit":
    process(line)
```

### 列表推导
```python
results = [y for x in data if (y := expensive(x)) is not None]
```

### 字典get默认值
```python
if (value := cache.get(key)) is not None:
    return value
```

---
*更新时间: {DATETIME_STR}*
