---
layout: post
title: Toggle Radio Buttons with jQuery
---

###HTML Code###

{% highlight html %}

<button id="toggle_button">Toggle</button><br>
<input type="radio" name="radio_name" value="One" checked="true">One<br>
<input type="radio" name="radio_name" value="Two">Two<br>

{% endhighlight %}

###JQuery Code###

{% highlight js %}
$('#toggle_button').click(function() {
         $('input[type="radio"]')
                    .not(':checked')
                    .prop("checked", true);
});
{% endhighlight %}
