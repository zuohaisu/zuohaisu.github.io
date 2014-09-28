---
layout: post
title: 议登录界面在移动端产品中的展现
description: "今天早晨产品经理提出了一个大胆的方案推进移动端产品用户系统的布局：在用户启动软件的时候，就展示登录界面，由此强化帐号概念。"
modified: 2013-05-31
tags: [产品经理]
image:
comments: true
share: true
categories: post
---

今天早晨产品经理提出了一个大胆的方案推进移动端产品用户系统的布局：在用户启动软件的时候，就展示登录界面，由此强化帐号概念。

简单的介绍一下我们的移动端产品。是一个媒体播放器，允许用户在线点播网络影音资源。

该方案一经提出，全场都陷入了沉思。负责实现的iOS和Android技术经理都表示了或多或少的不赞成，他们对于用户体验的考虑更多一些。

iOS Human Interface Guide有明确的提及：

> “Delay a login requirement for long as possible. Ideally, users should be able to navigate through much of your app and understand what they can do with it before logging in. When you ask users to log in before they can begin to use your app, it can make the start-up process seem longer.”
>   
> ——Stay Instantly, User Experience, iOS HIG 2011-10-12

大体是说，尽可能久的拖延登录界面，使得用户能够更快的体验产品的主要功能。

对于该条建议，我也抱有相当大的同感。由于手机软件的使用环境相对于PC软件更加复杂，变化更快，使得手机软件必须更加专注在最重要的功能上，而可有可无的功能就应该藏起来，让那些专家级的用户去慢慢挖掘。而我们的产品的最主要功能是影音播放，所以用户系统本身并不是最终要的功能，这和QQ的性质完全不同。QQ可以在一开始就强调登录界面，是因为登录是QQ产品使用流程中不可省略的步骤。QQ无法省略的环节，只能通过简化来弱化该步骤，使得用户更快的进入下一个环节。例如帮用户记录用户名和密码、帮用户自动登录、替用户自动切换输入框焦点等。

从战略角度上说，产品经理提出的方案确实很有新意，也很大胆；第一解决了用户登录入口的问题，第二从一个侧面推动了用户注册的问题。如果我们的产品有很强的用户粘性和更高的不可替代性，我觉得这样的方案在未来会成为推动公司进入新阶段的推力之一。