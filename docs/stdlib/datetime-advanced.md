# datetime高级用法

## 时区处理
```python
from datetime import datetime, timezone, timedelta
from zoneinfo import ZoneInfo

now_utc = datetime.now(timezone.utc)
now_shanghai = now_utc.astimezone(ZoneInfo('Asia/Shanghai'))
```

## 时间差计算
```python
delta = timedelta(days=7, hours=3)
future = now + delta
days_left = (deadline - now).days
```

## 格式化
```python
now.strftime('%Y-%m-%d %H:%M:%S')
datetime.strptime('2024-01-01', '%Y-%m-%d')
```

## ISO格式
```python
now.isoformat()
datetime.fromisoformat('2024-01-01T00:00:00+08:00')
```
