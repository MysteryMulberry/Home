# Git工作流最佳实践

## 分支策略

### Git Flow
- `main`: 生产分支
- `develop`: 开发分支
- `feature/*`: 功能分支
- `release/*`: 发布分支
- `hotfix/*`: 紧急修复分支

### Trunk-Based Development
- 主干开发，频繁集成
- 使用Feature Flag控制功能发布
- 短生命周期分支（<1天）

## Commit规范

### Conventional Commits
```
feat: 添加用户登录功能
fix: 修复密码验证逻辑错误
docs: 更新API文档
style: 代码格式调整
refactor: 重构数据库连接模块
test: 添加用户模块单元测试
chore: 升级依赖版本
```

## 常用操作

### 交互式变基
```bash
git rebase -i HEAD~3
```

### Cherry-pick
```bash
git cherry-pick abc123
```

### Stash管理
```bash
git stash push -m "WIP: feature-x"
git stash pop
git stash list
```

## Code Review要点
1. 检查逻辑正确性
2. 验证边界条件处理
3. 审查测试覆盖率
4. 确认文档同步更新
5. 评估性能影响

---
*更新时间: {DATETIME_STR}*
