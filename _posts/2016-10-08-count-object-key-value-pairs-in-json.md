---
layout: post
title: How to count number of key/value pairs in JSON Object
---

To count the number key/value pairs in a JSON object we need to convert an array. And then we can easily count the number of element in the array which is same as the number key value pairs in the json object.

`Object.keys()` returns an array whose elements are strings corresponding to the enumerable properties found in the object.

{% highlight js %}

function countObjectKeys(obj) { 
    return Object.keys(obj).length; 
}

//Usage 
var emp = {"firstName":"John", "lastName":"Doe"};
console.log(countObjectKeys(emp)); //2

{% endhighlight %}