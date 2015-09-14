---
title: Ember.merge()
---

{% highlight js %}
allSales: function() {
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
{% endhighlight %}
