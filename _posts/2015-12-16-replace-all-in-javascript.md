---
title: Replace all in JavaScript
layout: post
---

The JavaScript `.replace()` function will only replace the first instance if you use just two strings like this:

{% highlight js %}
var text = 'This is the blog of Adriaan, the worst blog in the universe'
text.replace('blog', 'life') // 'This is the life of Adriaan, the worst blog in the universe'
{% endhighlight %}

So to replace all occurences of `blog` you can use:

{% highlight js %}
text.replace(/blog/g, 'life')
{% endhighlight %}

But that is [30% slower than](https://jsperf.com/replace-vs-split-join-vs-replaceall/23) this:

{% highlight js %}
text.split('blog').join('life')
{% endhighlight %}
