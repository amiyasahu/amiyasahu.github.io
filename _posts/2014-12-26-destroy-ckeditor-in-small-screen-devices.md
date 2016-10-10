---
layout: post
title:  How to Destroy CKEditor in small screen devices
---

> The [CKeditor](http://ckeditor.com/ "CKeditor website") fires an event `instanceReady` once the instances are ready to be used. 

So we need to create a listener which will listen for this event. 

We will only execute the event handler if the browser window width is less than the some defined width for a small screen devices. 

> In Jquery the width of the browser window can be determined by `$.width()` method by calling on `window` object.

{% highlight html %}
<script type="text/javascript">
$(document).ready(function() {
    function destroyCKEditor(minWidth) {
        if (typeof CKEDITOR != 'undefined' 
            && $( window ).width() < minWidth) {
            CKEDITOR.on("instanceReady", function(event)
            {
               $.each(CKEDITOR.instances, function(index, instance) {
                    instance.destroy();
               });
            });
        };
    }
    //usage 
    //destroy ck editor in devices less than 768px wide 
    destroyCKEditor(768);
});
</script>
{% endhighlight %}

## How to use this for Question2Answer websites

If you are a owner of a [Question2Answer](http://www.question2answer.org) website and you wish to show the plain text editor to your users who is viewing the site on their mobile device, this would be the best way to go.

### Steps –

1. Login into your website as Admin
2. Navigate to Admin -> Layout
3. Paste the above code in Custom HTML at bottom of every page: section
4. You may change the value here given as per your requirement `destroyCKEditor(500);`. Here the 500 is the minimum allowed width, below which all the CKEditor instances will be destroyed
