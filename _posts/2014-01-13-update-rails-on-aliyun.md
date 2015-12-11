---
layout: post
title: 用Git更新阿里云上Rails项目
description: 
modified: 2014-01-13
tags: [开发, 部署, CentOS, Ruby, Rails]
comments: true
share: true
categories: post
---

[上一篇](/post/2014/01/10/deploy-rails-project-on-aliyun-centos-6/)记录了如何将rails代码部署到阿里云上。这一篇介绍代码版本升级的步骤。

第一步：将你的新版本代码推送到git服务器上去，我是推送到github的。

第二步：更新服务器上的代码
{% highlight bash %}
#找到跑在后台的进程，进程名称里一般会有ruby
ps -aux
#终止该进程，pid是在上面命令后找到的
kill -9 pid
#进入rails目录
cd your_project_dir
#用git更新代码
git fetch https://github.com/xxx/yyy.git
git -a .
git -commit -m "your_msg"
git pull https://github.com/xxx/yyy.git
#重启Rails服务器，之前可能会需要bundle或者rake之类的步骤
rails s -d
{% endhighlight %}

大功告成。