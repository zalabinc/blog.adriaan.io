---
layout: post
title: Ember.merge()
---

Sometimes you want to combine (merge, union) to array's into one. Here is an example with getting the sales of a user. The API does not support an `or`-request so we have to make two requests. We then `merge` those results back into one new array.

{% highlight js %}
import DS from 'ember-data';

export default DS.Model.extend({

  sales: function() {
    return Ember.merge(this.get('sellerSales'), this.get('buyerSales'));
  }.property('sellerSales', 'buyerSales'),
  
  sellerSales: function() {
    return this.store.query('sale', {
      seller: this.get('id')
    });
  }.property(),
  
  buyerSales: function() {
    return this.store.query('sale', {
      buyer: this.get('id')
    });
  }.property()
  
});
{% endhighlight %}

[Docs](http://emberjs.com/api/#method_merge) on Ember.merge()
