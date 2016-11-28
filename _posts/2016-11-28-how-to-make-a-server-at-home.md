---
layout: post
title: 在家用路由器内网搭建可以互联网访问的服务器
description: 
modified: 2016-11-28
tags: [技术, 部署, 开发]
image:
comments: true
share: true
categories: post
---
1. 将一台废旧的电脑安装linux系统（我安装了ubuntu 32位 16.04)，变成一台服务器
2. 用网线连接上内网路由器，并且绑定内网IP地址
3. 设置DMZ将外网访问转发到服务器
4. 注册一个DDNS服务，并且申请一个域名
5. 将域名和账号填入路由器设置里（我家用的是某米的路由器），如果成功会显示“成功启用”
6. 将服务器设置成常开，我的笔记本合上屏幕也不会休眠
7. 尝试用ssh访问这台服务器，如果能成功访问到，就说明DDNS与DMZ都正常工作