---
layout: post
title: How to turn off number input spinners in CSS3
---
Modern browsers add little up down arrows to number inputs called spinners.

You can turn them off visually like the below . This works in both Chrome and Firefox

{% highlight css %}
input[type=number]::-webkit-outer-spin-button,
input[type=number]::-webkit-inner-spin-button {
  -webkit-appearance: none;
  margin: 0;
}
input[type=number] {
  -moz-appearance: textfield;
}
{% endhighlight %}
