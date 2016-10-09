---
layout: post
title: Toggle Radio Buttons with jQuery
---

Are you looking for a piece of code where you need to toggle the radio button values. JQuery provices handful of methods by using which we can acomplish easily.
Here you go with step by step approach.

###Step 1. HTML Code###
Create two checkboxes and by default let one of them be checked. Then create a button which will act as a switch. When we click the button the radio button will toggle.
{% highlight html %}
<label>
	<input type="radio" name="car" value="Honda" checked>Honda
</label>
<label>
	<input type="radio" name="car" value="Benz">Benz
</label>

<button id="toggle_button">Toggle</button>
{% endhighlight %}

###Step 2. JQuery Code###

{% highlight js %}
$('#toggle_button').click(function() {
	$('input[name="car"]')	    //get all checkboxes
		.not(':checked')		   //if it is not checked
		.prop("checked", true);   //make it checked
});
{% endhighlight %}
