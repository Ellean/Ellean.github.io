---
layout: post
title: Currying 柯里化
categories: 技术参考 Tech.Ref.
tags: 
    - 参考
    - Ref.
    - 技术
    - Tech.
    - 柯里化
    - Currying
date: 2020-02-19 22:08:40
---

## 什么是柯里化

> 把 `接受多个参数的函数` 变换成 `接受一个单一参数（最初函数的第一个参数）的函数` ，并且 `返回接受余下的参数而且返回结果的新函数`
> -- 维基百科

翻译一下这段话：**把一个函数变成另一个函数**

那么前后有什么变化呢？

```js oldFunction 
let oldFunction = (one, two, three) => {
  return one + two + three
}

oldFunction(1, 2, 3)
// 6
```

```js newFunction
let newFunction = one => {
  return two => {
    return three => {
      return one + two + three
    }
  }
}

newFunction(1)(2)(3)
// 6
```

## 为什么要柯里化

> 又是一个坑。。🥺