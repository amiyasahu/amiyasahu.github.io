---
layout: post
title: Toggle Checkboxes using JQuery (Select All/Select None)
---

When user clicks `Select All` checkbox, the code first checks the status of checkbox with id `select-all`, and loops though each checkbox with class `checkbox` update their checked property to `true`. When it is clicked again then it will update their checked property to `false`.

### 1. HTML Code
{% highlight html %}
<input type="checkbox" id="select-all"/> Select All
<input type="checkbox" class="checkbox" name="chk[]" value="1"> 1
<input type="checkbox" class="checkbox" name="chk[]" value="2"> 2
<input type="checkbox" class="checkbox" name="chk[]" value="3"> 3
{% endhighlight %}
### 2. JQuery code
{% highlight js %}
$(document).ready(function() {
    $('#select-all').click(function(event) {
    	var btn = this, toStatus = btn.checked;
    	//loop through each checkbox
        $('.checkbox').each(function() { 
            $(this).prop('checked', toStatus);
        });
    });
});
{% endhighlight %}

Here is the live exaample
<script async src="//jsfiddle.net/amiya/wznx11gt/25/embed/js,html,result/"></script>
