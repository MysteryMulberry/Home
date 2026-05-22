# RESTful API设计规范

## URL设计
- 使用名词而非动词: `/users` 而非 `/getUsers`
- 使用复数形式: `/users` 而非 `/user`
- 嵌套资源: `/users/{id}/posts`
- 最多两层嵌套

## HTTP方法
| 方法 | 用途 | 幂等性 |
|------|------|--------|
| GET | 获取资源 | 是 |
| POST | 创建资源 | 否 |
| PUT | 全量更新 | 是 |
| PATCH | 部分更新 | 否 |
| DELETE | 删除资源 | 是 |

## 状态码
- 200: 成功
- 201: 创建成功
- 204: 删除成功（无内容）
- 400: 请求参数错误
- 401: 未认证
- 403: 无权限
- 404: 资源不存在
- 422: 验证失败
- 500: 服务器错误

## 分页
```json
{
  "data": [...],
  "pagination": {
    "page": 1,
    "per_page": 20,
    "total": 100,
    "total_pages": 5
  }
}
```

## 错误响应
```json
{
  "error": {
    "code": "VALIDATION_ERROR",
    "message": "Invalid email format",
    "details": [
      {"field": "email", "message": "Must be a valid email address"}
    ]
  }
}
```

---
*更新时间: {DATETIME_STR}*
