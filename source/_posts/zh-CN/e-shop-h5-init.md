---
layout: post
title: 基于 Nuxt + Vant 的自营电商项目(一)
categories:
    - 项目日志 Project Log
tags:
    - Vant
    - Nuxt.js
    - 电商
    - 项目
    - 前端
date: 2020-02-13 21:20:50
---

# 第一篇 搭建项目

<!-- more -->

## 1. 初始化 Nuxt

```shell Github/
$ npx create-nuxt-app <项目名>
```

## 2. 引入 Vant
安装 vant less less-loader

```shell <项目名>/
$ npm i -S vant 
$ npm i -D less less-loader
```

在 nuxt.config.js 文件里注册插件：

```JavaScript nuxt.config.js
build: {
  transpile: [/vant.*?less/],
  babel: {
    plugins: [
      [
        'import',
        {
          libraryName: 'vant',
          style: (name) => {
            return `${name}/style/less.js`
          }
        },
        'vant'
      ]
    ]
  }
}
```

## 3. 使用 Vant

{% tabs import method %}
<!-- tab 全局引用 -->
在 plugins 目录添加 vant.js 文件，全局引用 Vant 组件：

{% code plugin/vant.js lang:js %}
import Vue from 'vue'
import Vant from 'vant';
import 'vant/lib/vant-css/index.css'

Vue.use(Vant)
{% endcode %}

<!-- endtab -->

<!-- tab 局部引用 -->
在 页面 或者 模版 中局部引用 Vant 组建

{% code pages/index.vue lang:js %}
import { Button } from 'vant'
{% endcode %}

<!-- endtab -->
{% endtabs %}


