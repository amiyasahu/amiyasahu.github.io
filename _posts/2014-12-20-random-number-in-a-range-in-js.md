---
layout: post
title: Get random numebr with in a range in JQuery
---

To get random number between a range, we can make use of the `Math.random()` and `Math.floor()` function. 
{% highlight js %}
//returns random number between the min and max range
function getRandomNumber ( min , max ) {
	return  Math.floor(Math.random() * (max-min + 1)) + min ; 
}
//usage 
getRandomNumber(1 , 10) ; //a number between 1 and 10

{% endhighlight %}
