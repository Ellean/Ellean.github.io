---
layout: post
title: 在 CentOS Minimal 上配置 Samba
date: 2020-04-27 21:02:40
---

# 环境

虚拟机环境：Parallels Desktop 15.1.3-47255

宿主机环境：macOS 10.15.4

系统环境：CentOS 7.7 1908 Minimal

网卡模式：NAT

# 目的

~~安装 `Parallels Tools`~~
配置 `Samba` 一定程度上替代 `Parallels Tools`

<!-- more -->

# 问题与解决

## 完全没有网络

相对来说这个在意料之中，`Minimal` 安装的情况下，网络默认是关闭 `DHCP` 的。

### 开启方式（一）

```shell
nmtui
```

我盲猜是 `Network Management Terminal User Interface` 的缩写，出来以下界面：

![nmtui](https://tva1.sinaimg.cn/large/007S8ZIlly1ge8n9ww5jpj30zy0u0wgs.jpg)

话不多说，`Edit a connections`，这个还挺像 `Windows` 设置环境变量的窗口的：

![Edit_a_connection](https://tva1.sinaimg.cn/large/007S8ZIlly1ge8nd1vhswj30zt0u0djr.jpg)

继续，`Edit`，基本上就是这两个都如图：

![automatic](https://tva1.sinaimg.cn/large/007S8ZIlly1ge8ng4ubbdj31040u0n02.jpg)

返回……返回……返回……最后 `clear` 一下屏幕，蓝蓝的一片实在碍眼，现在可以了：

![ping_baidu.com](https://tva1.sinaimg.cn/large/007S8ZIlly1ge8nkxsjuoj30r80900wh.jpg)

### 开启方式（二）

重装 CentOS 标准版吧 🥺

## 安装、配置 `Samba`

```shell
yum -y install samba
```

```shell
vi /etc/samba/smb.conf
```

```shell
vi /etc/samba/smb.conf
```

配置 `[homes]` 中
 `browserable = YES`
 `valid user = root`或者其他你开心的用户
就好啦

## 坑

### 防火墙……

是的，要设置防火墙策略，但是，我选择关闭：

```shell
systemctl stop firewalld
```

### 启动 `Samba`

为啥之前不写？因为那是配置安装啊！

```shell
systemctl start smb.service
```

### 咋访问啊？IP呢？？？

这个简单，`ifconfig` 都不会吗？？？

嗯……很好，很 `Minimal`。

```shell
yum search ifconfig
```

冒出来什么工具你就装，好像是 `network_to0ls.x86_64` 吧 🤪

Done! 交作业！