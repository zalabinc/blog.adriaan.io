---
title: Ember Use findBy on PromiseArray
layout: post
redirect_from: /post/95822980964/ember-use-findby-on-promisearray/
---

How to do a `findBy` on an `PromiseArray` in Ember?

```js
export default Ember.ObjectController.extend({

  products: function() {
    return this.store.find('products');
  }.property(),

  product: function() {
    return this.get('products').findBy('default', true);
  }.property('products.isFulfilled')

});
```

The trick is to use the `isFulfilled` flag so it does not throw an error.

Ember < 2.0.0 (don't now the exact version)
