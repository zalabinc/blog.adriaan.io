---
title: Disable mouse gestures in Google Chrome on Mac
layout: post
---

![](https://cloud.githubusercontent.com/assets/1079135/10726981/b0bc6256-7bd6-11e5-9e6a-f29a8f2b723f.png)

If you hate this arrow as much as I do, then you want to disable it right away! Go to your terminal and run these commands:

{% highlight shell %}
defaults write com.google.Chrome AppleEnableSwipeNavigateWithScrolls -bool true
defaults write com.google.Chrome AppleEnableMouseSwipeNavigateWithScrolls -bool true
{% endhighlight %}

Then restart your Chrome and be happy.

### Before Mavericks
Before Mavericks this command was enought, but it does not work for your mouse in Mavericks, Yosemite and El Capitan.

{% highlight shell %}
defaults write com.google.Chrome AppleEnableSwipeNavigateWithScrolls -bool true
{% endhighlight %}

### Canary
For Canary you have to replace `com.google.Chrome` with `com.google.Chrome.canary`.

### Read more
[Ask Different question](http://apple.stackexchange.com/questions/21236/how-do-i-disable-chromes-two-finger-back-forward-navigation)
