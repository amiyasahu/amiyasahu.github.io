---
layout: post
title: How to Make a dropdown readonly using Jquery
---

<blockquote>
Dropdown (select element) is always read only. User do not edit it. User can select any of the option of its own chice. Unlike other html elements, it dont have a attribute which can make the element readony and prevent users to change its value. 
</blockquote>

So how do we do this, when we want to prevent the user not to edit its selected option. 

There is a little trick. Why can't we disable it.

Wait a second... 

But as we are disabling this field, the field will not be the part of the request when the form is submitted. 

We can do some work around for this.

So we need to use a hidden field to store disabled selected-option value. When the moment select element is disabled we need to create a hidden input field in the form and store the selected value. The moment it is enabled we need to restore the element with the value stored in the hidden field. 

Here you go with a code example -

###HTML code###
{% highlight html %}
<form action="#">
    <select id="choose" name="alpha">
        <option value="A">A</option>
        <option value="B">B</option>
        <option value="C">C</option>
    </select>
</form>

<button id="toggle">toggle enable/disable</button>
{% endhighlight %}
###JQuery code###
{% highlight js %}
jQuery(document).ready(function($) {
    var $select = $('#choose'), 
    name = $select.prop('name'), 
    $form = $select.parent('form');

	//store the name in the data attribute 
    $select.data('original-name', name);  

    $('#toggle').on('click', function(event) {

        if($select.prop('disabled')){
            //enable the element
            //remove the hidden fields if any
            $form.find('input[type="hidden"][name='+name+']')
            	 .remove(); 
            //restore the name and enable 
            $select.prop({name : name, 
            				disabled : false}); 
        } else {
            //disable it 
            var $hiddenInput = $('<input/>', 
            					{   type  : 'hidden', 
            						name  : name, 
            						value : $select.val()
            					});

			//append the hidden field to the form
            $form.append( $hiddenInput );  
            //change name and disbale 
            $select.prop({ name : name + "_1",
            				 disabled : true });
        }
    });
});
{% endhighlight %}

Here is a live example.
<script async src="//jsfiddle.net/amiya/qkjhs6fj/10/embed/html,js,result/"></script>