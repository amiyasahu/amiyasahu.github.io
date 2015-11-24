---
layout: post
title: Get random numebr with in a range in JQuery
---

{% highlight js %}
//function which gives random number between the min and max values 
function getRandomNumber ( min , max ) {
	return  Math.floor( Math.random() * ( max - min + 1) ) + min ; 
}
//usage 
var rand = getRandomNumber(1 , 1000) ; //random number between 1 and 1000
{% endhighlight %}
