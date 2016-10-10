---
layout: post
title:  Dealing with text nodes in JQuery
---

## How to know if the element is a text node or not

The below method will help you to check if the given element is a text node or not.

{% highlight js %}
function isTextNode(elem){
    // If this is a text node, return true.
    return( elem.nodeType === window.Node.TEXT_NODE );
}
{% endhighlight %}


## How to get all the text nodes in a particular element.

The below piece of code can help you in getting all the text nodes in a element identified by the selector.

{% highlight js %}
$('selector')
    .contents()
    .filter(function(){
        return this.nodeType === window.Node.TEXT_NODE 
                && $.trim(this.nodeValue) !== '';
    });
{% endhighlight %}
