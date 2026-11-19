---
title: Sticky Footer Styles
date: 2014-08-04 09:38:26
tags: 
  - CSS
  - Web
---

# Sticky Footer Styles

## 问题背景

页脚通常位于页面底部，但当页面内容较少时，页脚可能会悬浮在中间，导致页面下方出现空白区域，影响美观。为了解决这个问题，可以使用 CSS 技巧让页脚始终“粘附”在页面底部。

## HTML 结构

```html
<!DOCTYPE html>
<html>
  <body>
    <div id="wrap">
      <!-- 页面主要内容 -->
    </div>
    <div id="footer">
      <!-- 页脚内容 -->
    </div>
  </body>
</html>
```

## CSS 样式

```css
html, body {
  height: 100%; /* html 和 body 元素不能有 padding 或 margin */
}

/* 包裹页面内容的容器，用于推送页脚到底部 */
#wrap {
  min-height: 100%;
  height: auto !important;
  height: 100%;
  margin: 0 auto -60px; /* 负边距等于页脚高度 */
}

/* 设置页脚的固定高度 */
#footer {
  height: 60px;
  background-color: #f5f5f5;
}
```

## 效果说明

- `#wrap` 的负边距会将页脚“拉”到页面底部
- 页脚高度固定，页面内容不足时也不会出现空白
- 适用于响应式布局和简洁页面设计
