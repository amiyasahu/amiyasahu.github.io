---
layout: post
title: How to turn off Autocomplete for text input in HTML
---

The autocomplete attribute can be used to Enable/Disable the autocomplete feature of a HTML form element.

<strong>Note:</strong> The autocomplete attribute works with the following `<input>` types: `text`, `search`, `url`, `tel`, `email`, `password`, `datepickers`, `range`, and `color`.

This can be applied directly to the form to turn off the autocomplete features of all it child elements.

{% highlight html %}
<form action="..." autocomplete="off" method="post" name="my-form">
	[...]
</form>
{% endhighlight %}

Also this attribute can be applied to individual elements.

{% highlight html %}
<form action="..." method="post" name="my-form">
   <input autocomplete="off" name="text1" type="text" /> <!-- Off --> 
   <input autocomplete="on" name="text2" type="text" /> <!-- On -->
</form>
{% endhighlight %}