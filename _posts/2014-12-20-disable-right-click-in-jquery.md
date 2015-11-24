---
layout: post
title: Disable right click in JQuery
---

{% highlight js %}
$(document).ready(function(){
	$(document).on("contextmenu",function(e){
		return false;
	});
});
{% endhighlight %}
