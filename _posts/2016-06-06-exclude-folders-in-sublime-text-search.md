---
---

When you use the *Find in folder*-function of Sublime Text, you probaly hate the fact it is also searching in your `node_modules` folder. There is a nice feature in Sublime Text where you can specify which folders to exclude from your search.

Right-click on a folder and select *Find in folder...* (there will be input fields shown on the bottom), you will see the *Where*-input field. If is probably already filled in with the folder name you just right-clicked on. You can now add this after the folder into the field:

```
, -*/node_modules/*
```

That way your *Where*-field looks something like this:

```
/Users/Adriaan/MyCoolApp, -*/node_modules/*
```

If you use Ember.js, you probably want something like this:

```
/Users/Adriaan/MyCoolApp, -*/node_modules/*, -*/bower_components/*, -*/tmp/*
```
