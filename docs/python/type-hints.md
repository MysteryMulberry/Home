# Python类型标注进阶

## 基本类型
```python
def greet(name: str, times: int = 1) -> str:
    return (f"Hello, {name}! ") * times
```

## 泛型与容器
```python
from typing import List, Dict, Optional, Union

def process(items: List[int]) -> Dict[str, int]:
    return {"count": len(items), "sum": sum(items)}

def find(id: int) -> Optional[User]:
    return db.get(id)
```

## Protocol (结构化子类型)
```python
from typing import Protocol

class Drawable(Protocol):
    def draw(self) -> None: ...

def render(obj: Drawable):
    obj.draw()
```

## TypeVar和泛型函数
```python
from typing import TypeVar

T = TypeVar('T')

def first(items: list[T]) -> T:
    return items[0]
```

---
*更新时间: {DATETIME_STR}*
