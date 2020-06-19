---
layout: post
title: 微信小程序中动态CSS的支持
date: 2020-06-20 06:15:45
tags:
  - 微信小程序
  - 动态CSS
---

## 微信小程序不支持动态 CSS

在不考虑工程化和框架的情况下，微信小程序原生开发的情况下是不支持 `Stylus` / `Sass` 等动态 `CSS` 。

## 解决方案

1. 曲线救国

> 采用 `CSS` 自带的 变量功能

2. 奇技淫巧

> 利用元素的 `style` 属性将变量传入，在 `WXSS` 中即可引用到。

<!-- more -->

### 曲线救国

> 采用 `CSS` 自带的 变量功能

```CSS custom.wxss
page {
  --main-bg-color: #fff;
}

.card {
    background-color: var(--main-bg-color);
}
```

### 奇技淫巧

> 利用元素的 `style` 属性将变量传入，在 `WXSS` 中即可引用到。

```xml /pages/index/index.wxml
<view style="{{ style }}">
</view>
```

```JavaScript /pages/index/index.js
Page({
    data: {
        style: '--bg: red; --radius: 20rpx;'
    }
})
```

```CSS /pages/index/index.wxss
.card {
    background-color: var(--bg);
    border-radius: var(--radius)
}
```
