# SQL查询优化技巧

## 索引优化
- WHERE/JOIN/ORDER BY列建索引
- 避免在索引列上使用函数
- 复合索引遵循最左前缀
- 避免SELECT *

## 查询改写
```sql
-- 慢: 子查询
SELECT * FROM orders WHERE user_id IN (SELECT id FROM users WHERE active = 1);

-- 快: JOIN
SELECT o.* FROM orders o JOIN users u ON o.user_id = u.id WHERE u.active = 1;
```

## EXPLAIN分析
```sql
EXPLAIN ANALYZE SELECT * FROM large_table WHERE indexed_col = 'value';
```

## 常见问题
- N+1查询: 使用eager loading
- 全表扫描: 添加合适索引
- 临时表: 优化GROUP BY/ORDER BY

---
*更新时间: {DATETIME_STR}*
