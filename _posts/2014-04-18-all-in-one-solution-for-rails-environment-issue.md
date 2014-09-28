---
layout: post
title: 一招鲜解决各类奇葩rails错误
description: 
modified: 2014-04-18
tags: [开发, rails, ruby]
image:
comments: true
share: true
categories: post
---

前一段时间发现ruby-1.9.3已经说过期了，所以安装了最新的2.1.1，结果出现各种奇葩的错误。先说一下，我用的是Mac OS X 1.9.2的系统，Xcode也已经更新到最新。

1. Gem编译环境错误
ERROR: Failed to build gem native extension.
不管是用rails server, bundle, rake routes, gem list命令时都会出现，网上关于这个错误的讨论很多，我暂时没发现什么特别好的解释。但是用本文提供的方法就可以解决。

2. ruby的版本切换时出现不正常
我当时有1.9.3和2.1.1两个版本，用rvm info命令，看到rails-2.1.1@global，还在编译时看到了2.1.0的Gem文件夹，反正各种混乱。比如用rvm 1.9.3 default命令时说1.9.3不存在，然后重新安装1.9.3时安装了一个全新的1.9.3, 后面带的pxxx的编号有些差异。

3. 以上情况用加sudo命令时就没问题
这种时候让我更加纠结，难道运行个rails s也要加上sudo命令，输入个密码么？


出现了这种情况的时候，最好就是用我本文介绍的一招鲜，一了百了彻底解决。

运行下列命令
{% highlight bash %}
#将.rvm文件夹下的文件彻底删除
sudo rm -rf ~/.rvm/
{% endhighlight %}

然后重新安装rvm及你需要的ruby版本、对于ruby项目重新bundle。