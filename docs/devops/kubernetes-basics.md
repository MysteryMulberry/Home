# Kubernetes基础概念

## 核心对象
- **Pod**: 最小部署单元
- **Service**: 服务发现与负载均衡
- **Deployment**: 声明式应用部署
- **ConfigMap/Secret**: 配置管理

## 常用命令
```bash
kubectl get pods -A
kubectl describe pod <name>
kubectl logs -f <pod-name>
kubectl apply -f deployment.yaml
kubectl scale deployment/<name> --replicas=3
```

## Deployment示例
```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: web-app
spec:
  replicas: 3
  selector:
    matchLabels:
      app: web
  template:
    spec:
      containers:
      - name: web
        image: myapp:1.0
        ports:
        - containerPort: 8000
```

---
*更新时间: {DATETIME_STR}*
