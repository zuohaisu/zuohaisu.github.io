---
layout: post
title: Ruby on Rails常用指令备忘录
description: 
modified: 2013-07-21
tags: [开发, ruby, rails, shell, 菜鸟]
comments: true
share: true
categories: post
---

{% highlight bash %}
#查看版本号，order可以是任何命令，包括rvm，ruby，bundler，rails，gem等
order -v
#打开项目目录下的gemfile文件，将第一行的gem位置改为”http://ruby.taobao.org”，并运行下面的代码
gem sources -l #查看有哪些位置
gem sources -a http://ruby.taobao.org #添加淘宝镜像
gem sources -r https://rubygems.org #去掉亚马逊的源
#创建controller
rails generate controller controllerName
#在/app/controllers/生成一个welcome_controller.rb文件
#在/app/views/生成welcome/index.html.erb文件
#创建resource
rails generate resource resourceName
{% endhighlight %}

如果出现问题首先在运行了WEBrick服务的终端里找原因，会提示错误类型，里面可能会提示如何解决问题，由于创建resource的时候会创建数据库，有可能会遇到数据迁移的问题。