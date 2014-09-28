---
layout: post
title: 在CentOS 6上部署Ruby on Rails项目
description: 
modified: 2014-01-10
tags: [开发, 部署, CentOS, Ruby, Rails]
comments: true
share: true
categories: post
---

学习Ruby on Rails的口号喊了有半年多了，最近两周时间因为迫于生理原因（大家一定会误解了，想了解请看后记）密集的学习了一下。

完成了最基础的功能注册、登录、推荐书籍、修改书籍信息、借书、还书之后，就想着要部署到线上去。朋友推荐用heroku去做部署，也试了一下，amazon的网络墙得厉害，经常掉线。所以就放弃了这条路，等亚马逊云服务在国内稳定了，相信heroku就方便了。我有一个阿里云服务器，在国内速度还算可以啊，就想自己去折腾部署吧。（吐槽一下：虽然阿里云最近从69/月降价到55/月，但带宽限制也下降到了1Mbit，什么所谓的降价都是欺骗消费者，其实是变相提价带宽资源。）

**第一步**：一些工具的安装，包括rvm、git、nginx。

rvm的安装可以看[这篇文章](https://www.digitalocean.com/community/articles/how-to-install-ruby-on-rails-on-centos-6-with-rvm)，但是其中的有些步骤因为rvm版本的升级而失效，请一定要看下文章下面的评论第一条和第二条。

git和nginx的安装满大街都有，可以自己找。

**第二步**：安装完环境后，利用git从github把代码同步过来并设置访问权限。我的服务没什么特别的安全限制的，所以就设置成777

**第三步**：阿里云上搭建环境

{% highlight bash %}
#设置文件与目录的权限
chmod -R 777 your_project_dir
#设置生产环境
cd your_project_dir
rake RAILS_ENV=production
#数据迁移
rake db:migrate
#启动服务将服务放在后台
rails s -d #这里可以添加-p 80，将端口设置为80
{% endhighlight %}

**第四步**：配置nginx反向代理，这里最重要的一行是下面第7行; 然后重启nginx。大功告成！这样通过nginx实现了一个反向代理。这样通过nginx你还可以在同一台机器上部署其他项目。

{% highlight c linenos %}
server{
    listen 80;
    server_name your.domain.com; //你的域名
    index index.htm index.html index.html.erb;
    location /
    {
        proxy_pass http://localhost:3000; //我的默认端口是3000，所以这里的反向代理指向localhost:3000
    }
}
{% endhighlight %}

后记：
之所以说是生理原因，因为半年前赌咒说不写图书馆项目就不理发。发在朋友圈里了，不能食言。从夏天拖到了冬天，终于忍受不了长发的困扰就去理发了。让大家失望了，哈哈！感谢在这过程中给予我帮助的Sanvi、Harry、Haibao、小杰、水文。让这些资深的程序员陪着菜鸟玩实在是难为你们啦！