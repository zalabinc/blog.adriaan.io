---
title: How to create a shortcut in terminal for Mac for Sublime Text
layout: post
---

Copy and paste the code below in `~/.bash_profile`. You can edit the file by typing `nano ~/.bash_profile`

{% highlight bash %}
# Sublime Text alias
alias subl='/Applications/Sublime\ Text.app/Contents/SharedSupport/bin/subl'
{% endhighlight %}

For Sublime Text 2 it is

{% highlight bash %}
# Sublime Text alias
alias subl='/Applications/Sublime\ Text\ 2.app/Contents/SharedSupport/bin/subl'
{% endhighlight %}

Now you can type

{% highlight bash %}
$ subl ~/Downloads/some_file.txt
{% endhighlight %}
