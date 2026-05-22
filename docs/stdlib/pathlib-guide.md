# pathlib路径操作

## 基本操作
```python
from pathlib import Path
p = Path('/home/user/docs/file.txt')
p.name       # file.txt
p.stem       # file
p.suffix     # .txt
p.parent     # /home/user/docs
```

## 文件操作
```python
p = Path('data.csv')
content = p.read_text(encoding='utf-8')
p.write_text('hello world')
p.exists()
p.is_file()
```

## 遍历
```python
for f in Path('.').rglob('*.py'):
    print(f)
```

## 路径构建
```python
base = Path('/data')
config = base / 'configs' / 'app.yaml'
```
