---
layout: post
title: 在《Discover Meteor》书中249页有错误
description: 
modified: 2014-06-18
tags: [开发, javascript, meteor, bug]
image:
comments: true
share: true
categories: post
---

Meteor是一个优秀的框架，《Discover Meteor》是一本优秀的入门书籍。只是在249页的代码中有一个逻辑bug，原文如下：

{% highlight javascript %}

	//..
			attributes.class = 'post invisible';
			)
		});
	}
*/client/views/posts/post_item.js*

	//..
			var delta = post.position - newPosition; 
			)
		});
*/client/views/posts/post_item.js*