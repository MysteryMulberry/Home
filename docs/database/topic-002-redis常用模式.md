# Redis常用模式

## 缓存模式
```python
import redis
r = redis.Redis()

def get_with_cache(key, fetch_func, ttl=300):
    value = r.get(key)
    if value is None:
        value = fetch_func()
        r.setex(key, ttl, value)
    return value
```

## 分布式锁
```python
def acquire_lock(key, timeout=10):
    return r.set(key, 'locked', nx=True, ex=timeout)

def release_lock(key):
    r.delete(key)
```

## 限流器
```python
def rate_limit(key, max_requests=100, window=60):
    pipe = r.pipeline()
    now = time.time()
    pipe.zremrangebyscore(key, 0, now - window)
    pipe.zadd(key, {str(now): now})
    pipe.zcard(key)
    pipe.expire(key, window)
    _, _, count, _ = pipe.execute()
    return count <= max_requests
```

---
*更新时间: {DATETIME_STR}*
