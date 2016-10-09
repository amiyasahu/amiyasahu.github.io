---
layout: post
title: Cool horizontal devider in CSS
---
You can create a cool horizontal devider element (`hr`) using the below simple css code.

{% highlight css %}
@media screen {
  hr.devider {
    border: 0;
    height: 1px;
    background: -webkit-linear-gradient(left, rgba(0, 0, 0, 0), rgba(0, 0, 0, 0.5), rgba(0, 0, 0, 0));
    background: linear-gradient(left, rgba(0, 0, 0, 0), rgba(0, 0, 0, 0.5), rgba(0, 0, 0, 0));
    margin: 35px 0 30px 0;
  }
}
{% endhighlight %}

Here is a live example.

<script async src="//jsfiddle.net/amiya/pj4yf183/embed/html,css,result/"></script>