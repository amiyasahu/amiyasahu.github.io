---
layout: post
title: Intresting Javascript tricks
---

## Swap variables
{% highlight js %}
var a = 10 , b = 20 ; 
console.log("a = " + a + " , b = " + b);  // a = 10 , b = 20
b = [a, a = b][0];                        // swap the variables 
console.log("a = " + a + " , b = " + b);  // a = 20 , b = 10
{% endhighlight %}

## Truncate a value to a Integer in Javascript

| Usage       | Result
| `~~0.125`     | 0
| `~~1`         | 1
| `~~1.6`       | 1
| `~~"2.59"`    | 2
| `~~-2.8`      | -2 
| `~~"Apple"`   | 0
| `~~[]`        | 0
| `~~null`      | 0

Note -: It never returns NaN. If it fails, it just returns 0

## Check if given input is numeric in Javascript
{% highlight js %}
function isNumeric (arg) {
    return !isNaN(parseFloat(arg)) && isFinite(arg);
}
{% endhighlight %}

| Usage                  | Result
| `isNumeric(10)`         | true 
| `isNumeric(10.234)`     | true 
| `isNumeric(0.215)`      | true 
| `isNumeric('10')`       | true 
| `isNumeric('10.234')`   | true 
| `isNumeric('0.215')`    | true 
| `isNumeric('')`         | false 
| `isNumeric('Qwerty')`   | false 
| `isNumeric('43Agd')`    | false