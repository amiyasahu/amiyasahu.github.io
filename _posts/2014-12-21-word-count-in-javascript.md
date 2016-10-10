---
layout: post
title: Word count after trimming white spaces in Javascript
---

The below function can count the number of words in a line by ignoring the white space characters .

{% highlight js %}
function wordCount (str) {
    if(!!str)
        return str.trim().replace(/\s+/gi, ' ').split(' ').length;
    else 
        return 0;
}

//usage 
var str = "Hello There. How is the   weather     today in   India",
count = wordCount();
console.log(count); // 8
{% endhighlight %}
