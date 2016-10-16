---
layout: post
title: How to reset file input type in JQuery
---

If you want to reset the input type using traditional method will not work .
For doing so you `wrap()` a `<form>` around the element, call `reset()` on the newly created `form`, then remove the form using `unwrap()`

{% highlight js %}
function resetFileElement(e) {
  e.wrap('<form>').closest('form').get(0).reset();
  e.unwrap();
}
{% endhighlight %}
[Reference](http://stackoverflow.com/a/13351234/1691300) & [Live Example](http://jsfiddle.net/rPaZQ/)