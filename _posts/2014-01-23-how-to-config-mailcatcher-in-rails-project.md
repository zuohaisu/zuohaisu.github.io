---
layout: post
title: 如何在rails开发环境里里配置mailcather
modified: 2014-01-21
tags: [post, devise, rails, ruby, email]
image:
comments: true
share: true
categories: post
---

**Step One, install mailcatcher, type the command in terminal**
{% highlight bash %}
gem install mailcatcher
{% endhighlight %}

**Step Two, run mailcatcher, type the command in terminal**
{% highlight bash %}
mailcatcher
{% endhighlight %}

**Step Three, change the configuration in /config/environments/development.rb**
{% highlight ruby linenos %}
config.action_mailer.raise_delivery_errors = true
config.action_mailer.default_url_options = { :host => 'localhost:3000' }
config.action_mailer.delivery_method = :smtp
config.action_mailer.perform_deliveries = true
config.action_mailer.default :charset => "utf-8"
config.action_mailer.smtp_settings = {
  :address => "localhost",
  :port => 1025,
  :domain => "localhost:3000"
}
{% endhighlight %}

**Step Four, open http://127.0.0.1:1080 in browser and now you can test the email sending function.**