---
---

Maybe you want to have a logo with the same url showing something different on production and staging. Or you want to have different `robots.txt` files because you don't want to give robots permision on you non-production environment (like staging or acceptance).

In Ember.js you can edit the tree like this:

```js
// ember-cli-build.js

'use strict';

const EmberApp = require('ember-cli/lib/broccoli/ember-app');
const stew = require('broccoli-stew');

module.exports = (defaults) => {
  const ENV = require('./config/environment')(process.env.EMBER_ENV);

  const app = new EmberApp(defaults, {
    // Your options...
  });

  // Make sure the correct robots.txt is there
  let tree = app.toTree();
  if (ENV.environment === 'production') {
    tree = stew.rm(tree, 'robots-disallow.txt');
    tree = stew.rename(tree, 'robots-allow.txt', 'robots.txt');
  } else {
    tree = stew.rm(tree, 'robots-allow.txt');
    tree = stew.rename(tree, 'robots-disallow.txt', 'robots.txt');
  }
  return tree;
};
```

You need to add `'use strict';` on top of the file if you use `let` variables.

Make sure you install [broccoli-stew](https://github.com/stefanpenner/broccoli-stew) by installing it via `npm install broccoli-stew --save-dev`.
