# Python测试框架对比

## pytest (推荐)
```python
def test_addition():
    assert 1 + 1 == 2

@pytest.fixture
def sample_data():
    return [1, 2, 3]

def test_with_fixture(sample_data):
    assert len(sample_data) == 3
```

## unittest (标准库)
```python
import unittest

class TestMath(unittest.TestCase):
    def test_add(self):
        self.assertEqual(1 + 1, 2)
```

## 测试覆盖率
```bash
pytest --cov=myapp --cov-report=html
```

## Mock使用
```python
from unittest.mock import patch

@patch('module.external_api')
def test_with_mock(mock_api):
    mock_api.return_value = {'status': 'ok'}
    result = my_function()
    assert result is not None
```

---
*更新时间: {DATETIME_STR}*
