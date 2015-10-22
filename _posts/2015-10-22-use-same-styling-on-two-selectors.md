---
title: Use the same style definitions twice without extend
layout: post
---

In `sass` or `scss` you can use `extend`-function to merge selectors together.
This is useful for some cases, but when you just want to define the styling on
two different selectors you maybe want a different behaviour.

The problem is as follows.

{% highlight scss %}
%button {
  color: red;
}

.button {
  @extend %button;
}

.button-desktop-only {
  @media (min-width:  1200px) {
    @extend %button;
  }
}
{% endhighlight %}

Results in the following `css`:

{% highlight css %}
.button,
.button-desktop-only {
  color: red;
}
{% endhighlight %}

But you want to have this result:

{% highlight css %}
.button {
  color: red;
}
.button-desktop-only {
  @media (min-width:  1200px) {
    color: red;
  }
}
{% endhighlight %}

How to solve this?  If just want to copy some styling to another selector you 
can use the `mixin`-function like this:

{% highlight scss %}
@mixin button() {
  border: none;
}

.button {
  @include button();
}

@media (min-width: 1200px) {
  .button-desktop-only {
    @include button();
  }
}
{% endhighlight %}

What will result in this `css`:

{% highlight css %}
.button {
  color: red;
}

@media (min-width: 1200px) {
  .button-desktop-only {
    color: red;
  }
}
{% endhighlight %}
