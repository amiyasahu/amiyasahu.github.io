---
layout: post
title: Intresting Javascript tricks
---

## Swap variables
{% highlight js %}
var a = 10 , b = 20 ; 
console.log("a = " + a + " , b = " + b);  // a = 10 , b = 20
b = [a, a = b][0];                        // swap the variables 
console.log("a = " + a + " , b = " + b);  // a = 20 , b = 10
{% endhighlight %}