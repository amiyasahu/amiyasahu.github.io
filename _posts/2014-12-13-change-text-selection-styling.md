---
layout: post
title: How to change text selection styling in CSS3
---
The ::selection CSS pseudo-element applies rules to the portion of a document that has been highlighted (e.g., selected with the mouse or another pointing device) by the user.

Note that Only a small subset of CSS properties can be used in a rule using ::selection in its selector: color, background, background-color and text-shadow.

{% highlight css %}
::-moz-selection {
     background: #24890d;
     color: #fff;
     text-shadow: none;
}
::selection {
     background: #24890d;
     color: #fff;
      text-shadow: none;
}
{% endhighlight %}
