# Python设计模式实践指南

## 创建型模式

### 单例模式
```python
class Singleton:
    _instance = None

    def __new__(cls):
        if cls._instance is None:
            cls._instance = super().__new__(cls)
        return cls._instance
```

### 工厂方法模式
```python
from abc import ABC, abstractmethod

class Creator(ABC):
    @abstractmethod
    def create(self):
        pass

class ConcreteCreatorA(Creator):
    def create(self):
        return ConcreteProductA()
```

## 结构型模式

### 适配器模式
```python
class Adapter:
    def __init__(self, adaptee):
        self.adaptee = adaptee

    def request(self):
        return self.adaptee.specific_request()
```

### 装饰器模式
```python
def logging_decorator(func):
    def wrapper(*args, **kwargs):
        print(f"调用: {func.__name__}")
        result = func(*args, **kwargs)
        print(f"返回: {result}")
        return result
    return wrapper
```

## 行为型模式

### 观察者模式
```python
class Observable:
    def __init__(self):
        self.observers = []

    def attach(self, observer):
        self.observers.append(observer)

    def notify(self, message):
        for observer in self.observers:
            observer.update(message)
```

### 策略模式
```python
class Context:
    def __init__(self, strategy):
        self.strategy = strategy

    def execute(self, data):
        return self.strategy(data)
```

---
*更新时间: {DATETIME_STR}*
