---
layout: post
title: Get current Mouse pointer coordinates using JQuery
---

{% highlight js %}
$(document).ready(function() {
	$(document).mousemove(function(e)
	{
		console.log( "X : " + e.pageX );
		console.log( "Y : " + e.pageY );
	});
});
{% endhighlight %}
