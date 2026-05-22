# CI/CD流水线设计

## GitHub Actions示例

### 基础Python CI
```yaml
name: CI
on: [push, pull_request]
jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: actions/setup-python@v5
        with:
          python-version: '3.12'
      - run: pip install -r requirements.txt
      - run: pytest --cov
      - run: ruff check .
```

### Docker构建与发布
```yaml
name: Docker Build
on:
  push:
    tags: ['v*']
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: docker/login-action@v3
        with:
          registry: ghcr.io
          username: ${{ github.actor }}
          password: ${{ secrets.GITHUB_TOKEN }}
      - uses: docker/build-push-action@v5
        with:
          push: true
          tags: ghcr.io/${{ github.repository }}:${{ github.ref_name }}
```

## 流水线阶段
1. **Lint**: 代码风格检查
2. **Test**: 单元测试 + 集成测试
3. **Build**: 构建产物
4. **Security**: 安全扫描
5. **Deploy**: 部署到环境

## 最佳实践
- 保持流水线快速（<10分钟）
- 缓存依赖加速构建
- 使用矩阵测试多版本
- 失败时发送通知
- 保护主分支需要PR通过CI

---
*更新时间: {DATETIME_STR}*
