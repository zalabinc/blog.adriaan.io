---
title: How to trim whitespace on save in Sublime Text
layout: post
---

When you use `git` with other developers together you maybe want to trim all the whitespace at the end of every line.
So when you hit `return` or `enter` with some indenting and you save the file `git` will see the whitespaces as a new commit.
You probably don't want that, so you can automatically trim the whitespace on save in Sublime Text.

Go to `SublimeText` > `Preferences` > `User Settings` and add the following line:

{% highlight js %}
{
  ...
  "trim_trailing_white_space_on_save": true
}
{% endhighlight %}

Works for Sublime Text version 2 and 3. Enjoy!
