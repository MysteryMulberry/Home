# Python异步编程模式详解

## 概述
Python的asyncio库为编写并发代码提供了强大支持。本文总结常用的异步编程模式。

## 核心概念

### 事件循环 (Event Loop)
```python
import asyncio

async def main():
    print("Hello")
    await asyncio.sleep(1)
    print("World")

asyncio.run(main())
```

### 协程 (Coroutine)
```python
async def fetch_data(url):
    await asyncio.sleep(0.5)
    return f"Data from {url}"
```

## 常用模式

### 1. 并发执行多个任务
```python
async def concurrent_tasks():
    tasks = [fetch_data(f"url_{i}") for i in range(10)]
    results = await asyncio.gather(*tasks)
    return results
```

### 2. 带超时的任务
```python
async def with_timeout():
    try:
        result = await asyncio.wait_for(fetch_data("url"), timeout=5.0)
    except asyncio.TimeoutError:
        print("操作超时")
```

### 3. 生产者-消费者模式
```python
async def producer(queue):
    for i in range(20):
        await queue.put(i)
    await queue.put(None)

async def consumer(queue):
    while True:
        item = await queue.get()
        if item is None:
            break
        await asyncio.sleep(0.1)
        queue.task_done()
```

## 最佳实践
- 避免在异步函数中使用阻塞调用
- 使用 `asyncio.to_thread` 包装同步IO操作
- 合理设置并发限制（Semaphore）
- 正确处理异常和取消

---
*更新时间: {DATETIME_STR}*
