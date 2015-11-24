---
layout: post
title: Cool horizontal row in CSS
---
You can create a cool horizontal row element (hr) using the below css code .

{% highlight css %}
@media screen {
  hr {
    border: 0;
    height: 1px;
    background: -webkit-linear-gradient(left, rgba(0, 0, 0, 0), rgba(0, 0, 0, 0.5), rgba(0, 0, 0, 0));
    background: linear-gradient(left, rgba(0, 0, 0, 0), rgba(0, 0, 0, 0.5), rgba(0, 0, 0, 0));
    margin: 35px 0 30px 0;
  }
}
{% endhighlight %}
