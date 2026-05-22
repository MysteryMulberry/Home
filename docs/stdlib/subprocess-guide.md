# subprocess进程管理

## run (推荐)
```python
import subprocess
result = subprocess.run(
    ['git', 'status'],
    capture_output=True,
    text=True,
    timeout=10
)
print(result.stdout)
print(result.returncode)
```

## Popen (高级控制)
```python
proc = subprocess.Popen(
    ['python', 'script.py'],
    stdin=subprocess.PIPE,
    stdout=subprocess.PIPE,
    stderr=subprocess.PIPE
)
stdout, stderr = proc.communicate(input=b'data')
```

## 管道连接
```python
p1 = subprocess.Popen(['ls'], stdout=subprocess.PIPE)
p2 = subprocess.Popen(['grep', 'py'], stdin=p1.stdout, stdout=subprocess.PIPE)
output = p2.communicate()[0]
```

## 安全注意事项
- 避免shell=True（命令注入风险）
- 使用列表传参而非字符串
- 设置timeout防止挂起
