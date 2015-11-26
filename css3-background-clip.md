CSS3 Background Clip – The Visible Range of Background
======================================================

The background-clip property specifies the painting area of the background image
or background color.

The default value is:

```css
background-clip: border-box;
```

This means that the background is clipped to the border box, i.e. the background
is visible under the element's border.

Other values for background clipping:

`padding-box` – clips the background at the outside edge of the element's
padding, i.e. the background is not visible under the element's border

`content-box` – clips the background at the edge of the content box, i.e. does
not apply the padding or border

If you are still not sure how to use the `border-`, `padding-` and `content-box`
values, take a look at the [box-sizing](<css3-box-sizing.md>) property example.

See a live example at
[codepen.io/machal/pen/yamFI](<http://codepen.io/machal/pen/yamFI>).

Browser Support
---------------

Let's put it simply: IE9+. Polyfills for IE8 do not even exists and there is no
wonder… It's hard to find an example where they would be necessary.
