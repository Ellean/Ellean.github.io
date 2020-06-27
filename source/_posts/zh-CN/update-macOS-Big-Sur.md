---
layout: post
title: 升级 macOS Big Sur 踩坑记录
date: 2020-06-28 06:15:30
---

# `VS Code`

## 高亮失效
1. 问题在自定义字体，若将字体设置恢复默认，高亮正常，则问题一致.
> 解决办法：
> 重新安装目标字体后，重新设置字体

# `iTerm2`

## 关机卡死
## 打开 终端（zsh）即假死，卡在光标，`prompt` 一直无法出现。

> 解决办法：
> 关闭 偏好 - 高级 - 会话 - 开启会话恢复
> Disable `Enable session restoration` in **Preference - Advanced - Session**