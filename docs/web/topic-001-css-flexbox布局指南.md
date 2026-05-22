# CSS Flexbox布局指南

## 容器属性
```css
.container {
    display: flex;
    flex-direction: row | column;
    justify-content: flex-start | center | space-between | space-around;
    align-items: stretch | center | flex-start | flex-end;
    flex-wrap: nowrap | wrap;
    gap: 10px;
}
```

## 项目属性
```css
.item {
    flex: 1;              /* 等分空间 */
    flex: 0 0 200px;      /* 固定宽度 */
    align-self: center;   /* 单独对齐 */
    order: -1;            /* 排序 */
}
```

## 常见布局
- 水平居中: `justify-content: center`
- 垂直居中: `align-items: center`
- 等分布局: 子元素 `flex: 1`
- 侧边栏: 主区域 `flex: 1`, 侧栏固定宽度

---
*更新时间: {DATETIME_STR}*
