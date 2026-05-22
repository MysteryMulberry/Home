# logging日志系统

## 基本配置
```python
import logging

logging.basicConfig(
    level=logging.INFO,
    format='%(asctime)s [%(levelname)s] %(name)s: %(message)s',
    handlers=[
        logging.FileHandler('app.log'),
        logging.StreamHandler()
    ]
)
logger = logging.getLogger(__name__)
```

## 日志级别
```python
logger.debug('Debug info')
logger.info('Normal operation')
logger.warning('Something unexpected')
logger.error('Operation failed')
logger.critical('System failure')
```

## 结构化日志
```python
import json_log_formatter

formatter = json_log_formatter.JSONFormatter()
handler = logging.StreamHandler()
handler.setFormatter(formatter)
```

## 最佳实践
- 使用 `__name__` 作为logger名称
- 避免在循环中频繁打日志
- 异常时使用 `logger.exception()` 自动记录堆栈
