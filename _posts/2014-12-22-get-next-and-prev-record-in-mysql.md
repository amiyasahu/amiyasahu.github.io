---
layout: post
title: Get Next or Previous record in MySQL
---

Query to get Next record in MySQL

{% highlight sql %}
SELECT * FROM foo WHERE id = (SELECT MIN(id) FROM foo WHERE id > 4)
{% endhighlight %}

Query to get Previous record in MySQL

{% highlight sql %}
SELECT * FROM foo WHERE id = (SELECT MAX(id) FROM foo WHERE id < 4)
{% endhighlight %}
