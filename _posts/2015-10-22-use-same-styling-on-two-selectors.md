---
title: Use the same style definitions twice without extend in SASS
---

In `sass` or `scss` you can use `extend`-function to merge selectors together.
This is useful for some cases, but when you just want to define the styling on
two different selectors you maybe want a different behaviour.

The problem is as follows.

```scss
%button {
  color: red;
}

.button {
  @extend %button;
}

.button-desktop-only {
  @media (min-width:  1200px) {
    @extend %button;
  }
}
```

Results in the following `css`:

```css
.button,
.button-desktop-only {
  color: red;
}
```

But you want to have this result:

```css
.button {
  color: red;
}
.button-desktop-only {
  @media (min-width:  1200px) {
    color: red;
  }
}
```

How to solve this?  If just want to copy some styling to another selector you 
can use the `mixin`-function like this:

```scss
@mixin button() {
  color: red;
}

.button {
  @include button();
}

@media (min-width: 1200px) {
  .button-desktop-only {
    @include button();
  }
}
```

What will result in this `css`:

```css
.button {
  color: red;
}

@media (min-width: 1200px) {
  .button-desktop-only {
    color: red;
  }
}
```
