---
layout: post
title: Detect JQuery AJAX Requests with PHP
---

```php

// returns true if the request is made with XMLHttpRequest header 
function isXhr() {
    return $_SERVER['HTTP_X_REQUESTED_WITH'] === 'XMLHttpRequest';
}

//Usage 
if( isXhr() ) {
    echo "The AJAX Request is made from JQuery ";
} else {
    echo "The AJAX Request might not be made from JQuery ";
}

```
