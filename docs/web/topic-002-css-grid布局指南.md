# CSS Grid布局指南

## 基本用法
```css
.grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    grid-template-rows: auto 1fr auto;
    gap: 20px;
}
```

## 命名区域
```css
.layout {
    display: grid;
    grid-template-areas:
        "header header header"
        "sidebar main main"
        "footer footer footer";
    grid-template-columns: 200px 1fr 1fr;
}
```

## 响应式
```css
.grid {
    grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
}
```

---
*更新时间: {DATETIME_STR}*
