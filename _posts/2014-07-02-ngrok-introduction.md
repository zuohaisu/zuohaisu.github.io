---
layout: post
title: 使用ngrok让本地运行的应用获得在线地址
description: 介绍ngrok的使用实例
modified: 2014-06-18
tags: [开发, javascript, meteor, 测试, 本地环境]
image:
comments: true
share: true
categories: post
---

最近在开发微信公众号的应用时遇到的一个现实问题，在本地运行的应用如何与微信公众号进行线上联调呢？微信公众号需要验证线上的接口有效性。此时ngrok大有作为。ngrok是一款可以使本地应用获得一个线网临时域名。

以Mac为例，将ngrok下载到本地，ngrok.zip是一个不到5M的单文件压缩包，解压之后是一个隐藏文件。用终端进入所在文件夹并用命令
“./ngrok 3000”，表示你将获得一个映射到本地localhost:3000的URL地址。启动之后，等到Tunnel Status显示为online时你会得到http和https两个映射到localhost:3000的链接，我本次获得的是“17cdaf5f.ngrok.com”，二级域名的位置字符串会随即变化，只在当次连接有效。此时你可以尝试用浏览器访问你获得的这个地址试试，神奇发生了。

除此之外，ngrok的终端窗口中还会显示该地址每次收到的请求状态，很方便测试时进行调试。如果需要退出，和其他的终端程序一样，用Ctrl+C就退出了。