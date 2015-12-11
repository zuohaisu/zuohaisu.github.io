---
layout: post
title: 重装服务器之后ssh连接时报错
description: "WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED"
modified: 2013-05-31
tags: [运维, 开发, 阿里云]
image:
comments: true
share: true
categories: post
---

今天重装了一台阿里云服务器，用之前的ssh连接的方式连接服务器遇到了以下错误，此时只需要用编辑器去删除掉和11.121.123.129有关的那一行即可。

{% highlight bash %}
#重装了系统之后连接
ssh root@11.121.123.129 
#报错了！
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that the RSA host key has just been changed.
#进入该文件去删除掉11.121.123.129这一行有关的信息
vim ~/.ssh/known_hosts
{% endhighlight %}

此时重连会发现已经正常了。