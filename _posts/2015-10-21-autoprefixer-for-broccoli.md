---
title: How to automaticly add css prefixes with Brocolli or EmberJS
layout: post
---

Ember uses the Broccoli build tool to build the `css` and `js`-files. You can ofcourse use Broccoli without EmberJS. 

Here is an example copy pasted out of the `Brocfile.js` file of my current project (without EmberJS):

{% highlight js %}
// Prefix the css
var prefixedCss = autoprefixer(css, {
  browsers: ['ie 9-11', 'last 2 versions']
});

// Merge and export the whole thing
module.exports = mergeTrees([prefixedCss, js]);
{% endhighlight %}

Where `css` is the Broccoli tree with the already compiled sass to css files.
In the `browsers`-object you can specify which browser you want prefixes for.
[More docs](https://github.com/ai/browserslist#queries) on the browsers object.

For Broccoli you can use the [npm module](https://www.npmjs.com/package/broccoli-autoprefixer)
by [sindresorhus](https://github.com/sindresorhus).
See the [broccoli-autoprefixer GitHub-repo](https://github.com/sindresorhus/broccoli-autoprefixer).

### Note on EmberJS
In EmberJS you should head to the ember-cli addon [ember-cli-autoprefixer](https://www.npmjs.com/package/ember-cli-autoprefixer)
