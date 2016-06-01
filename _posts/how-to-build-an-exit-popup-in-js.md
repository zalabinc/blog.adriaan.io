---
---

```js
const wait = 30000;

// Don't show the popup immediately, so put it in a timeout
const timeout = window.setTimeout(() => {

  // This can not be an arrow function because it is an event listner
  document.addEventListener('mouseout', function showPopup(event) {
    if (event.toElement == null && event.relatedTarget == null && event.clientY <= 0) {

      // Show the exit popup
      this.get('show')();

      // Remove the event listner so the popup is only showed once
      this.removeEventListener('mouseout', showPopup, false);
    }
  }, false);
}, wait);

// Abort when something happens (a user logs in for example)
function abort() {
  window.clearTimeout(timeout);
}

// Put the dialog logic here
function show() {
  window.alert('This is your exit popup');
}
```
