---
---

This cost me some minutes of my life. I was using `display: flex` on a `div` in my code with `justify-content: space-between`:

```html
<div>
  <p>Small text</p>
  <p><input type="submit" value="Do something" class="button"></p>
</div>
```

But it aligned like this:

![](/images/posts/flex-box-strange.png)

The `scss` looked not so strange, so I put everything in a [jsfiddle](https://jsfiddle.net/harianus/fczkLc93/2/) to figure out, but is showed correctly.

```scss
div {
  @include clearfix;
  width: 300px;
  border: 1px solid orange;
  display: flex;
  align-items: center;
  justify-content: space-between;
  
  p {
    border: 1px solid green;
  }
}
```

When comparing again I saw one small difference, there was this `@include clearfix` mixin. So I updated the [jsfiddle](https://jsfiddle.net/harianus/fczkLc93/1/) and there it was. The strange gap after the button.

This `clearfix` *(from Twitter Bootstrap)* caused the strange alignment with `justify-content: space-between`:

```scss
@mixin clearfix() {
  &::after {
    content: "";
    display: table;
    clear: both;
  }
}
```

After removing this `clearfix` it looked like this:

![](/images/posts/flex-box-good.png)

So the `::after` element is also considered part of the flexbox. This makes sense of course, but I totally missed it. Hopefully you don't.
