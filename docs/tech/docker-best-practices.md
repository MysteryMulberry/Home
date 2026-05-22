# Docker最佳实践

## 镜像优化

### 多阶段构建
```dockerfile
FROM python:3.12 AS builder
WORKDIR /app
COPY requirements.txt .
RUN pip install --user -r requirements.txt

FROM python:3.12-slim
COPY --from=builder /root/.local /root/.local
COPY . /app
WORKDIR /app
CMD ["python", "main.py"]
```

### 减小镜像体积
- 使用 `slim` 或 `alpine` 基础镜像
- 合并RUN指令减少层数
- 使用 `.dockerignore` 排除不必要文件
- 清理包管理器缓存

## 安全实践
- 不以root用户运行应用
- 固定基础镜像版本标签
- 定期扫描镜像漏洞
- 不在镜像中存储密钥

## Docker Compose
```yaml
version: '3.8'
services:
  web:
    build: .
    ports:
      - "8000:8000"
    depends_on:
      - db
    environment:
      - DATABASE_URL=postgresql://db:5432/mydb
  db:
    image: postgres:16-alpine
    volumes:
      - pgdata:/var/lib/postgresql/data
volumes:
  pgdata:
```

---
*更新时间: {DATETIME_STR}*
