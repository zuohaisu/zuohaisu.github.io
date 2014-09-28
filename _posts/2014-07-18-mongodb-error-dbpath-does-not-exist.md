---
layout: post
title: mongodb遇到dbpath (/data/db) does not exist如何解决
description: 用homebrew安装mongodb后启动mongod出现找不到数据库目录的错误，如何解决
modified: 2014-06-18
tags: [开发, rails, ruby, mongodb, 测试, 本地环境]
image:
comments: true
share: true
categories: post
---

环境：Mac 10.9

今天用rails配合mongoid用mongodb作为数据库时，遇到了一个报错：Moped::Errors::ConnectionFailure in Posts#index。网上说是因为没有启动mongodb，所以我就试着启动mongodb。先用homebrew升级到最新的mongodb，发现启动后报错如下：
{% highlight bash %}
  mongod --help for help and startup options
  2014-07-18T16:08:54.403+0800 [initandlisten] MongoDB starting : pid=10296 port=27017 dbpath=/data/db 64-bit host=hs-mac-air
  2014-07-18T16:08:54.403+0800 [initandlisten] db version v2.6.3
  2014-07-18T16:08:54.403+0800 [initandlisten] git version: nogitversion
  2014-07-18T16:08:54.403+0800 [initandlisten] build info: Darwin minimavericks.local 13.2.0 Darwin Kernel Version 13.2.0: Thu Apr 17 23:03:13 PDT 2014; root:xnu-2422.100.13~1/RELEASE_X86_64 x86_64 BOOST_LIB_VERSION=1_49
  2014-07-18T16:08:54.403+0800 [initandlisten] allocator: tcmalloc
  2014-07-18T16:08:54.404+0800 [initandlisten] options: {}
  2014-07-18T16:08:54.404+0800 [initandlisten] exception in initAndListen: 10296
  *********************************************************************
   ERROR: dbpath (/data/db) does not exist.
   Create this directory or give existing directory in --dbpath.
   See http://dochub.mongodb.org/core/startingandstoppingmongo
  *********************************************************************
  , terminating
  2014-07-18T16:08:54.405+0800 [initandlisten] dbexit:
  2014-07-18T16:08:54.405+0800 [initandlisten] shutdown: going to close listening sockets...
  2014-07-18T16:08:54.406+0800 [initandlisten] shutdown: going to flush diaglog...
  2014-07-18T16:08:54.406+0800 [initandlisten] shutdown: going to close sockets...
  2014-07-18T16:08:54.406+0800 [initandlisten] shutdown: waiting for fs preallocator...
  2014-07-18T16:08:54.406+0800 [initandlisten] shutdown: lock for final commit...
  2014-07-18T16:08:54.406+0800 [initandlisten] shutdown: final commit...
  2014-07-18T16:08:54.406+0800 [initandlisten] shutdown: closing all files...
  2014-07-18T16:08:54.407+0800 [initandlisten] closeAllFiles() finished
  2014-07-18T16:08:54.407+0800 [initandlisten] dbexit: really exiting now
{% endhighlight %}

翻看了一些stackoverflow上的文章后发现因为homebrew将mongodb.conf放在了/usr/local/etc/mongodb.conf这个位置，但是mongod启动时默认查找的/etc/mongodb.conf这个位置，而且默认的dbpath是在/data/db这个目录下。以非root用户身份其实是进入不了这个目录的，一定会遇到权限问题。mkdir无法直接创建/data目录，一定需要用sudo，但即便用sudo mkdir创建了/data/db目录后也没有解决权限的问题。所以还是不要在这条路上继续越陷越深了。

我换了个思路想了一下，既然没有数据库所在文件夹，那么给他指定一个就可以了。所以启动时我用了mongod --dbpath myDbPath启动后，一切正常了。rails项目也可以正常访问了。