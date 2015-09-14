---
title: Ember Use findBy on PromiseArray
layout: post
---

How to do a `findBy` on an `PromiseArray` in Ember?

{% highlight js %}
export default Ember.ObjectController.extend({

  products: function() {
    return this.store.find('products');
  }.property(),

  product: function() {
    return this.get('products').findBy('default', true);
  }.property('products.isFulfilled')

});
{% endhighlight %}

Ember < 2.0.0 (don't now the exact version)
