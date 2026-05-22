# Python并发编程模式

## threading
```python
from threading import Thread, Lock

lock = Lock()
results = []

def worker(data):
    with lock:
        results.append(process(data))

threads = [Thread(target=worker, args=(d,)) for d in data_list]
for t in threads:
    t.start()
for t in threads:
    t.join()
```

## concurrent.futures
```python
from concurrent.futures import ThreadPoolExecutor, ProcessPoolExecutor

with ThreadPoolExecutor(max_workers=4) as executor:
    futures = [executor.submit(process, item) for item in items]
    results = [f.result() for f in futures]
```

## asyncio + aiohttp
```python
import aiohttp
import asyncio

async def fetch(session, url):
    async with session.get(url) as resp:
        return await resp.text()

async def main():
    async with aiohttp.ClientSession() as session:
        tasks = [fetch(session, url) for url in urls]
        results = await asyncio.gather(*tasks)
```

---
*更新时间: {DATETIME_STR}*
