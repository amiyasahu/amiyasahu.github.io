---
layout: post
title: Difference between window.onload and $(document).ready()
---

The ready event occurs after the HTML document has been loaded (when the document is ready to be manipulated i.e browser has build the DOM tree ), while the onload event occurs later, when all content (e.g. images and other resources) also has been loaded.

The onload event is a standard event in the DOM, while the ready event is specific to jQuery. The purpose of the ready event is that it should occur as early as possible after the document has loaded, so that code that adds functionality to the elements in the page doesn't have to wait for all content to load.

###window.onload Syntax###

{% highlight js %}
$(window).load(function () {
         console.log("window load complete");
});

window.onload = function () {
         console.log("window load complete");
}
{% endhighlight %}

###$(document).ready() Syntax###

{% highlight js %}
$(document).ready(function () {
          console.log("document is ready.");
});
//short-hand 
$(function(){
    console.log("document is ready.");
});
{% endhighlight %}