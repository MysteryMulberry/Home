# 正则表达式进阶

## 常用模式
```python
import re

email = r'[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}'
url = r'https?://[\w.-]+(?:\.[\w]+)*(?:/[\w.-]*)*'
ipv4 = r'\d{1,3}(?:\.\d{1,3}){3}'
```

## 命名分组
```python
pattern = r'(?P<year>\d{4})-(?P<month>\d{2})-(?P<day>\d{2})'
m = re.match(pattern, '2024-01-15')
m.groupdict()  # {'year': '2024', 'month': '01', 'day': '15'}
```

## 替换回调
```python
def upper_repl(m):
    return m.group(1).upper()

result = re.sub(r'_(\w)', upper_repl, 'hello_world_test')
# helloWorldTest
```

## 性能优化
- 预编译: `pattern = re.compile(r'...')`
- 避免回溯: 使用非贪婪量词或原子组
