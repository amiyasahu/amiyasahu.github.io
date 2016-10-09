---
layout: post
title: Best Way to check Falsy values in Javascript
---

In Javascript world `undefined`, `null`, `0`, `false`, `NaN`, `''` (empty string) are all considered as false values.

So while coding if you want to check if a variable have a falsy value or not you need check the variable against all of these. Your code would look messed up if you keep comparing against all of these. 

Luckly, there is an easy way. You can apply negation operation on the variable twice (eg. `!!variable`), which will convert the variable value to appropriate boolean equivalent.

{% highlight js %}

function trueFalseCheck (variable) {
	if( !!variable ) {
	    console.log("True");
	} else {
	    console.log("False");
	}
}

trueFalseCheck(null);       //False
trueFalseCheck('');         //False
trueFalseCheck(0);          //False
trueFalseCheck(undefined);  //False
trueFalseCheck(false);      //False
trueFalseCheck(NaN);        //False

trueFalseCheck(true);		//True
trueFalseCheck('Amiya'); 	//True
trueFalseCheck(10); 		//True

{% endhighlight %}
