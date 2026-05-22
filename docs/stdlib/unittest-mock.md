# unittest.mock测试替身

## 基本Mock
```python
from unittest.mock import Mock, patch

m = Mock()
m.return_value = 42
assert m() == 42
m.assert_called_once()
```

## patch装饰器
```python
@patch('module.external_api')
def test_with_mock(mock_api):
    mock_api.return_value = {'status': 'ok'}
    result = my_function()
    assert result is not None
```

## MagicMock
```python
from unittest.mock import MagicMock

m = MagicMock()
m.method(1, 2, key='value')
m.method.assert_called_with(1, 2, key='value')
```

## side_effect
```python
m = Mock()
m.side_effect = [1, 2, Exception('error')]
m()  # 1
m()  # 2
m()  # raises Exception
```
