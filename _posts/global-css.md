---
title: Global CSS
date: 2014-08-03 08:56:59
tags: 
  - CSS
  - Web
---

# Global CSS

## 为什么需要 Global CSS？

由于各浏览器都有自身默认的样式，且不同浏览器的默认样式会有些不同。为了方便起见，在写 CSS 时，首先会使用 CSS Reset 清除浏览器的默认样式，以避免干扰。

此外，网页整体风格的样式（如取消所有链接的下划线）也通常放在 CSS 文件开头。因此，可以将 CSS Reset 与通用样式合并，形成 Global CSS，作为网站统一使用的基础样式。

## 常见的 CSS Reset 工具

### 1. [Eric CSS Reset](http://meyerweb.com/eric/tools/css/reset/index.html)

```css
/* http://meyerweb.com/eric/tools/css/reset/ v2.0 | 20110126 License: none (public domain) */
html, body, div, span, applet, object, iframe, h1, h2, h3, h4, h5, h6, p, blockquote, pre, a, abbr, acronym, address, big, cite, code, del, dfn, em, img, ins, kbd, q, s, samp, small, strike, strong, sub, sup, tt, var, b, u, i, center, dl, dt, dd, ol, ul, li, fieldset, form, label, legend, table, caption, tbody, tfoot, thead, tr, th, td, article, aside, canvas, details, embed, figure, figcaption, footer, header, hgroup, menu, nav, output, ruby, section, summary, time, mark, audio, video {
  margin: 0;
  padding: 0;
  border: 0;
  font-size: 100%;
  font: inherit;
  vertical-align: baseline;
}
/* HTML5 display-role reset for older browsers */
article, aside, details, figcaption, figure, footer, header, hgroup, menu, nav, section {
  display: block;
}
body {
  line-height: 1;
}
ol, ul {
  list-style: none;
}
blockquote, q {
  quotes: none;
}
blockquote:before, blockquote:after, q:before, q:after {
  content: '';
  content: none;
}
table {
  border-collapse: collapse;
  border-spacing: 0;
}
```

### 2. YUI Reset

```css
/* YUI 3.17.2 (build 9c3c78e) Copyright 2014 Yahoo! Inc. */
html {
  color: #000;
  background: #FFF;
}
body, div, dl, dt, dd, ul, ol, li, h1, h2, h3, h4, h5, h6, pre, code, form, fieldset, legend, input, textarea, p, blockquote, th, td {
  margin: 0;
  padding: 0;
}
table {
  border-collapse: collapse;
  border-spacing: 0;
}
fieldset, img {
  border: 0;
}
address, caption, cite, code, dfn, em, strong, th, var {
  font-style: normal;
  font-weight: normal;
}
ol, ul {
  list-style: none;
}
caption, th {
  text-align: left;
}
h1, h2, h3, h4, h5, h6 {
  font-size: 100%;
  font-weight: normal;
}
```

### 3. csslab Reset

```css
html, body, div, span, applet, object, iframe, h1, h2, h3, h4, h5, h6, p, blockquote, pre, a, abbr, acronym, address, big, cite, code, del, dfn, em, font, img, ins, kbd, q, s, samp, small, strike, sub, sup, tt, var, dl, dt, dd, ol, ul, li, fieldset, form, label, legend, table, caption, tbody, tfoot, thead, tr, th, td, article, aside, dialog, figure, header, footer, hgroup, menu, nav, section, time, mark, audio, video {
  margin: 0;
  padding: 0;
  border: 0;
  outline: 0;
  font-weight: inherit;
  font-style: inherit;
  font-size: 100%;
}
article, aside, nav, section, dialog, figure, header, footer, hgroup {
  display: block;
}
legend {
  display: none;
}
:focus {
  outline: 0;
}
table {
  border-collapse: collapse;
  border-spacing: 0;
}
caption, th, td {
  text-align: left;
  font-weight: normal;
}
a img, iframe {
  border: none;
}
ul {
  list-style: none;
}
input, textarea, select, button {
  font-size: 100%;
  font-family: inherit;
}
```
