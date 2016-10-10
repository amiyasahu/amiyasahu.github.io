---
layout: post
title:  Clear input Field on Focus using JQuery
---

This piece of code will clear the text input field on focus if the field is not changed by the user.

### HTML code
{% highlight html %}
<input type="text" id="username" data-default-value="username" value="username">
{% endhighlight %}

### JQuery code
{% highlight js %}
jQuery(document).ready(function ($) {
    var $field = $('#username'), 
        defaultValue = $field.data('default-value');
    $field.on('focus', function (event) {
        var $this = $(this);
        if ($this.val().trim() === defaultValue) $this.val('');
    });
    $field.on('focusout', function (event) {
        var $this = $(this);
        if ($this.val().trim() === '') $this.val(defaultValue);
    });
});
{% endhighlight %}

Here is a live example. 
<script async src="//jsfiddle.net/amiya/xd5tus6d/4/embed/html,js,result/"></script>