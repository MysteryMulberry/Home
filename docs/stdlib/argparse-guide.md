# argparse命令行解析

## 基本用法
```python
import argparse

parser = argparse.ArgumentParser(description='My CLI tool')
parser.add_argument('input', help='Input file path')
parser.add_argument('-o', '--output', default='out.txt')
parser.add_argument('-v', '--verbose', action='store_true')
parser.add_argument('-n', '--count', type=int, default=1)
args = parser.parse_args()
```

## 子命令
```python
subparsers = parser.add_subparsers(dest='command')
add_parser = subparsers.add_parser('add')
add_parser.add_argument('files', nargs='+')

list_parser = subparsers.add_parser('list')
list_parser.add_argument('--all', action='store_true')
```

## 自定义类型
```python
def positive_int(value):
    iv = int(value)
    if iv <= 0:
        raise argparse.ArgumentTypeError(f"{value} is not positive")
    return iv

parser.add_argument('-n', type=positive_int)
```
