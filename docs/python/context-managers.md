# 上下文管理器深入理解

## 基于类的实现
```python
class DatabaseConnection:
    def __init__(self, url):
        self.url = url

    def __enter__(self):
        self.conn = connect(self.url)
        return self.conn

    def __exit__(self, exc_type, exc_val, exc_tb):
        self.conn.close()
        return False
```

## 基于生成器的实现
```python
from contextlib import contextmanager

@contextmanager
def database_connection(url):
    conn = connect(url)
    try:
        yield conn
    finally:
        conn.close()
```

## 异步上下文管理器
```python
class AsyncClient:
    async def __aenter__(self):
        self.session = aiohttp.ClientSession()
        return self

    async def __aexit__(self, *args):
        await self.session.close()
```

---
*更新时间: {DATETIME_STR}*
