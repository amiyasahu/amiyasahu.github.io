---
layout: post
title: Difference between == and === in Javascript
---

The == (or !=) operator performs an automatic type conversion if needed . The === (or !==) operator will not perform any conversion. It compares both the value and type, which could be considered faster than == .

###Few Examples###

{% highlight js %}
[10] === 10     // is false
[10]  == 10     // is true
'10' == 10      // is true
'10' === 10     // is false
[]   == 0       // is true
[] ===  0       // is false
'' == false     // is true 
'' === false    // is false
true == "a"     // is false
{% endhighlight %}
