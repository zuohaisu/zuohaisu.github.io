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

	//..	attributes: function() {		var post = _.extend({}, Positions.findOne({postId: this._id}), this); var newPosition = post._rank * POST_HEIGHT;		var attributes = {};		if (_.isUndefined(post.position)) { 
			attributes.class = 'post invisible';		} else {			var delta = post.position - newPosition; 			attributes.style = "top: " + delta + "px";			if (delta === 0)				attributes.class = "post animate" 		}		Meteor.setTimeout(function() {			Positions.upsert(				{postId: post._id},				{$set: {position: newPosition}}
			)
		});		return attributes; 
	}	//..{% endhighlight %}
*/client/views/posts/post_item.js*如果使用了这段代码，那么页面上的post就全部消失了，因为代码将所有attributes.class都预设为‘post invisible’。这里需要调换if-else区块内的代码，变成如下即可恢复正常：{% highlight javascript %}

	//..	attributes: function() {		var post = _.extend({}, Positions.findOne({postId: this._id}), this); var newPosition = post._rank * POST_HEIGHT;		var attributes = {};		if (_.isUndefined(post.position)) { 
			var delta = post.position - newPosition; 			attributes.style = "top: " + delta + "px";			if (delta === 0)				attributes.class = "post animate" 		} else {			attributes.class = 'post invisible';		}		Meteor.setTimeout(function() {			Positions.upsert(				{postId: post._id},				{$set: {position: newPosition}}
			)
		});		return attributes; 	}	//..{% endhighlight %}
*/client/views/posts/post_item.js*