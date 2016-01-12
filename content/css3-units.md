New CSS3 Units – `rem`, `vw`, `vh`
==================================

### `rem`

This is a size that corresponds with the `font-size` value at the root, i.e the
`<html>` element. The “root-em” is thus just a variant of the well-known `em`
unit. Unlike the standard `em` units, `rem` units are not based on the font size
of the parent element.

Font size of the `<html>` element is usually set in browsers to correspond with
`16px`.

If you set all sizes that relate to typography (or the layout in general) in
`rems`, you can then easily scale a document just by changing the value of the
`html { font-size: … }` property, thus creating elastic layouts.

Not unlike the example above, you can also change the overall document font size
using [media query](css3-media-queries.md), thus scaling the layout itself.

### Example

Set all sizes of a document using the `rem` unit. If you set all H1 headings to
`1.5rem`, the actual font size will be 1,5 × `16px` – therefore `24px`.

```css
h1 {
  font-size: 1.5rem;
}
```

If we then decide to set the base font size in media query to 25px if the
viewport is 801 pixels or wider,…

```css
@media (min-width: 801px) {
  html {
    font-size: 25px;
  }
}
```

… all elements set in `rem` units will increase their sizes. The `<h1>` heading
will then be 38 pixels (`25px` × 1,5).

You can see a live example at: [cdpn.io/e/mnbaA](http://cdpn.io/e/mnbaA)

### Browser Support

IE9+. It is also possible to create a pixel fallback for older browsers:

```css
font-size: 24px;
font-size: 1.5rem;
```

It is better to have a fallback generated automatically using a CSS
preprocessor.

Here is more about browser support: [caniuse.com/rem](http://caniuse.com/rem)

Viewport Units: `vw`, `vh`, `vmin`, `vmax`
------------------------------------------

They allow us to define CSS sizes relative to the viewport size - in other words
”the width or height of the window”.

-   `vw` – stands for “viewport width” – `1vw` is 1% of the viewport width
-   `vh` – stands for “viewport height” – `1vh` is 1% of the viewport height
-   `vmin` – stands for “viewport minimum” – represents the shortest dimension
    (`1vw` or `1vh`)
-   `vmax` – stands for “viewport maximum” – represents the longest dimension
    (`1vw` or `1vh`)

### Practical Example

Unlike percentage, viewport units do not relate to the size of the direct parent
but to the width and height of the browser window instead. We can literally do
magic that was once possible just by using CSS hacks or Javascript.

Let's show it on a simple example - stretching the height of a layout to the
full height of the browser window:

```css
.container {
  width: 100vh;
}
```

### Browser Support

The latest versions of all browsers except Opera Mini are compatible with these
units: [caniuse.com/viewport-units](http://caniuse.com/viewport-units)

But don't celebrate just yet:

-   IE9 uses `vm` instead of `vmin`.
-   IE10 does not understand `vmax`.
-   Safari on iOS6 and 7 experience several viewport unit bugs. Take a look at
    [caniuse.com/viewport-units](http://caniuse.com/viewport-units).
-   IE8, Android Browser up to version 4.3 and Opera Mini do not support these
    units at all.

So be careful when using these units.
