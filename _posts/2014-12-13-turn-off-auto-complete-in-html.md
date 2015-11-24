---
layout: post
title: How to turn off number input spinners in CSS3
---
The autocomplete attribute can be used to Enable/Disable the autocomplete feature of a HTML form element .

<strong>Note:</strong> The autocomplete attribute works with the following &lt;input&gt; types: text, search, url, tel, email, password, datepickers, range, and color.

This can be applied directly to the form to turn off the autocomplete features of all it child elements .
E.g
{% highlight html %}
<form action="..." autocomplete="off" method="post" name="form1">
	[...]
</form>
{% endhighlight %}
Also this attribute can be applied to individual elements . E.g
{% highlight html %}
<form action="..." method="post" name="form1">
   Name: <input autocomplete="off" name="text1" type="text" /> 
   Address: <input autocomplete="on" name="text2" type="text" /> <!-- turns on autocomplete -->
   Phone: <input autocomplete="off" name="text3" type="text" /> 
   <input name="Submit" type="Submit" value="Submit" />
</form>
{% endhighlight %}