---
layout: post
title: Active Record切换到MongoDB时遇到的错误
description: 
modified: 2014-04-22
tags: [开发, rails, ruby, mongodb]
image:
comments: true
share: true
categories: post
---

今天将数据库换成MongoDB了，在切换的时候也遇到了一些官网上没说清楚的地方。后来到处找也没找到问题，不过最终我还是仔细摸索后找到了解决方案。

首先说一下我的环境 *ruby-2.0.0*, *rails 4.1.0*

最先遇到的一个疑问在官网上遇到疑惑

{% highlight bash %}
# 我先运行了自动配置代码
rails g mongoid:config
{% endhighlight %}

运行完成后，还是要按照文档要求在 myapp/config/application.rb 里删掉 require "rails/all"，并且替换成：
{% highlight ruby %}
require "action_controller/railtie"
require "action_mailer/railtie"
require "active_resource/railtie"
require "rails/test_unit/railtie"
# require "sprockets/railtie" # Uncomment this line for Rails 3.1+
{% endhighlight %}

官方文档里说Rails 3.1+的版本要将第五行取消注释，实际上还应该将第三行注释。完成后的样子是这样的：
{% highlight ruby %}
require "action_controller/railtie"
require "action_mailer/railtie"
# require "active_resource/railtie"
require "rails/test_unit/railtie"
require "sprockets/railtie" # Uncomment this line for Rails 3.1+
{% endhighlight %}

这个时候运行rails s还是会遇到很多问题，我遇到了method_missing' undefined method active_record' 这样的错误，网上大部分都会提到一个解决方案，将config/environments/development.rb 和 test.rb中的两行注释掉：
{% highlight ruby %}
# config.active_record.mass_assignment_sanitizer = :strict
# config.active_record.auto_explain_threshold_in_seconds = 0.5
{% endhighlight %}

但我根本就没有这两行，后来在网上找到一个大神说出现这类错误一般和Active Record有关，所以我到config/environments/development.rb 和 test.rb里面所有带有active_record的配置项全部注释掉了，问题迎刃而解。