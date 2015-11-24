---
layout: post
title: Best Way to check Falsy values in Javascript
---

In Javascript `undefined, null, 0, false, NaN, '' ` (empty string) are all falsy .

So while coding if you want to check if a variable have a falsy value or not you need check the variable against all of these . Which is not good all the time . Here is a damn easy way . 

{% highlight js %}

function trueFalseCheck (variable) {
	if( !!variable ) {
	    console.log("True");
	} else {
	    console.log("False");
	}
}

trueFalseCheck(null);  //False
trueFalseCheck('');   //False
trueFalseCheck(0);  //False
trueFalseCheck(undefined);  //False
trueFalseCheck(false);  //False
trueFalseCheck(NaN);  //False

trueFalseCheck(true); //True
trueFalseCheck('Amiya Sahu'); //True
trueFalseCheck(10); //True

{% endhighlight %}
