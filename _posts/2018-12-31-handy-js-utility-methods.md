---
layout: post
title: Handy JavaScript Utility Methods
---

## Update Object state and return a new object by merging the socond onto the first one

{% highlight js %}
const updateObj = (oldObject, newObject) => {
  return {
    ...oldObject, 
    ...newObject
  };
};

// usage 
let obj = { key1: "value1", key2 : "value2" };
obj = updateObj(obj, { key2 : "value3" });
console.log(obj); // {key1: "value1", key2: "value3"}

{% endhighlight %}
