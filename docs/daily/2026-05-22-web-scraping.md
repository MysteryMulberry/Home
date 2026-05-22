# Web数据采集技巧

## 常用工具
- **requests**: HTTP请求库，简单高效
- **BeautifulSoup**: HTML解析，适合简单页面
- **Playwright**: 浏览器自动化，处理动态内容
- **Scrapy**: 专业爬虫框架，大规模采集

## 最佳实践
1. 遵守robots.txt规则
2. 设置合理的请求间隔
3. 使用User-Agent伪装
4. 处理异常和重试
5. 数据清洗与验证

## 示例: 使用requests + BeautifulSoup
```python
import requests
from bs4 import BeautifulSoup

resp = requests.get('https://example.com', timeout=10)
soup = BeautifulSoup(resp.text, 'html.parser')
titles = [h.text for h in soup.find_all('h2')]
```

---
*更新时间: {DATETIME_STR}*
