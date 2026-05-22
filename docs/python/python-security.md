# Python安全编程

## 输入验证
```python
import re

def validate_email(email):
    pattern = r'^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$'
    return bool(re.match(pattern, email))

def sanitize_input(text):
    return re.sub(r'[<>&'"]', '', text)
```

## 密码处理
```python
import hashlib
import secrets
import bcrypt

def hash_password(password: str) -> str:
    salt = bcrypt.gensalt()
    return bcrypt.hashpw(password.encode(), salt).decode()

def verify_password(password: str, hashed: str) -> bool:
    return bcrypt.checkpw(password.encode(), hashed.encode())
```

## SQL注入防护
```python
# 错误: 字符串拼接
query = f"SELECT * FROM users WHERE name = '{name}'"

# 正确: 参数化查询
cursor.execute("SELECT * FROM users WHERE name = %s", (name,))
```

## 安全随机数
```python
token = secrets.token_urlsafe(32)
```

---
*更新时间: {DATETIME_STR}*
