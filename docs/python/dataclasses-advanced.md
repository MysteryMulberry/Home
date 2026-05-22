# dataclass高级用法

## 基本用法
```python
from dataclasses import dataclass, field

@dataclass
class User:
    name: str
    age: int
    tags: list[str] = field(default_factory=list)
    active: bool = True
```

## frozen dataclass (不可变)
```python
@dataclass(frozen=True)
class Point:
    x: float
    y: float

    def distance_to(self, other: 'Point') -> float:
        return ((self.x - other.x)**2 + (self.y - other.y)**2)**0.5
```

## 继承
```python
@dataclass
class Employee(User):
    department: str = ""
    salary: float = 0.0
```

## 转换
```python
from dataclasses import asdict, astuple

user = User("Alice", 30)
d = asdict(user)
t = astuple(user)
```

---
*更新时间: {DATETIME_STR}*
