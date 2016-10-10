---
layout: post
title:  How to check if an element exists in an array in Javascript
---

The below function can efficiently check whether an element exists in the array or not

{% highlight js %}
if (!Array.prototype.elemetExists) {
    Array.prototype.elemetExists = function (string) {
        return !!~this.indexOf(string);
    };
}

//usage 
var fruits = ['Apple' , 'Banana' , 'Orange' , 'Mango'];
console.log(fruits.elemetExists('Banana'));  //true 
console.log(fruits.elemetExists('Lichi'));  //false
{% endhighlight %}
