---
layout: post
title:  How to delete a remote tag in git
---

If you need to delete a remote tag named – `oldtag` use the below command

{% highlight shell %}
git tag -d oldtag
git push origin :refs/tags/oldtag
{% endhighlight %}
