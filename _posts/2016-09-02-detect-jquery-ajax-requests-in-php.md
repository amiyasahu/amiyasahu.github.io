---
layout: post
title: Detect JQuery AJAX Requests with PHP
---

When you make a AJAX call to the server using JQUery, it adds a special header along with the request. 

So you can check on the server side against this header.

If the header *HTTP_X_REQUESTED_WITH* is present and is equal to *XMLHttpRequest*, then the AJAX call is made via jQuery.

{% highlight php%}
<?php
// returns true if the request is made with XMLHttpRequest header 
function isXhr() {
    return $_SERVER['HTTP_X_REQUESTED_WITH'] === 'XMLHttpRequest';
}

// Usage 

if(isXhr()) {
    echo "The AJAX Request is made from JQuery ";
} else {
    echo "The AJAX Request might not be made from JQuery ";
}
{% endhighlight %}
