---
layout: post
title:  How to get text nodes in JQuery
---

{% highlight js %}
$('selector')
    .contents()
    .filter(function(){
        return this.nodeType === window.Node.TEXT_NODE 
                && $.trim(this.nodeValue) !== '';
    });
{% endhighlight %}
