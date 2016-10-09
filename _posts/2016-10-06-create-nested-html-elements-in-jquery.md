---
layout: post
title: How to create nested HTML elements in JQuery
---

###JQuery code###
{% highlight js %}
var $elem = $('body div.main');
$elem.append(
            $('<div/>', {'class': 'wrapper'}).append(
                $('<div/>', {'class': 'inner'}).append(
                    $('<span/>', {text: 'Some text'})
                )
            ).append(
                $('<div/>', {'class': 'inner'}).append(
                    $('<span/>', {text: 'Other text'})
                )
            )
        );
{% endhighlight %}

###Result###
{% highlight html %}
<div class="main">
	<div class="wrapper">
		<div class="inner">
			<span>Some text</span>
		</div>
		<div class="inner">
			<span>Other text</span>
		</div>
	</div>
</div>
{% endhighlight %}
###Fiddle Example###
<script async src="//jsfiddle.net/amiya/9kggv7r7/4/embed/js,html,result/"></script>