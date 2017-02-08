Sometimes you have to get a variable from a nested object like this

```js
const toys = {
  muppets: {
    ernie: {
      head: 'wide'
    }
  }
}
```

If you are not sure if the complete object exist, you will have to do something like this:

```js
const ernieHead = (toys && toys.muppets && toys.muppets.ernie && toys.muppets.ernie.head) ? toys.muppets.ernie.head : undefined;
// Do more with ernieHead...
```

With Ember you can use the [`get`-function](http://emberjs.com/api/#method_get):

```js
const ernieHead = get(toys, 'toys.muppets.ernie.head');
```

So in a controller it would be like this:

```js
import Ember from 'ember';
const { Controller, get } = Ember;

export default Controller.extend({
  getToys() {
    const ernieHead = get(toys, 'toys.muppets.ernie.head');
    // Do more with ernieHead...
  }
});
```
