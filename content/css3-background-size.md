CSS3 Background Size
====================

This specifies the size of the background within an element.

Syntax
------

```css
background-size:
  (cover/contain)
  _vertical_size_
  _horizontal_size_;
```

The default value is `background-size: auto auto`, which tells the browser to
keep the original size of the image.

As with other CSS properties, we can set the width and height simultaneously:
`background-size: auto`.

### `cover` and `contain`

The key word `cover` tells the browser to cover the whole area of an element.
`contain`, on the other hand, tells the browser to show the whole image.

`background-size: cover` is typically used to make sure an image covers the
whole website background – see an example at
[alistapart.com/d/supersize-that-background-please/index3.html](http://alistapart.com/d/supersize-that-background-please/index3.html)

`background-size: contain` is typically used when placing an icon as the
background of an element that resizes according to various screen resolutions
and when you want to use double or triple the size of an image for
high-resolution displays. See
[studiopress.com/design/css-background-size-graphics.htm](http://www.studiopress.com/design/css-background-size-graphics.htm)

Tip: If you intend to work with icons this way, consider using a vector solution
(SVG or font icons).
[css-tricks.com/icon-fonts-vs-svg/](http://css-tricks.com/icon-fonts-vs-svg/).

### Size in `px` or Percentage

The *vertical_size* and *horizontal_size* values can be defined in standard
CSS units: `px`, `em` etc.

When using percentage, the values are relative to the width or height of the
element to which the property is applied. For example, stretching a gradient
background to the full width and one-half of the height of an element would look
like this:

```css
background:
  linear-gradient(to bottom, transparent, black)
  no-repeat bottom;
background-size:
  100
```

Take a look at a live example at
[cdpn.io/e/cmpjE](http://cdpn.io/e/cmpjE).

And do not forget that background width and height are based on how the
[background-origin](css3-background-origin.md) property is set. Thus, by
default the `padding-box` and `background-size` properties are calculated either
from the inner edge or from the content of the element.

### Multiple Background Images

If you are using [multiple background images](css3-multiple-backgrounds.md),
simply use a comma-separated list of values:

```css
background-size: 50% auto, auto;
```

Browser Support
---------------

The `background-size` property is supported by all contemporary browsers except
IE8. See
[caniuse.com/background-img-opts](http://caniuse.com/background-img-opts).

### `background-size` in IE8

There is no universal solution to this problem, however, depending on the
particular situation, you can choose from one of four approaches:

Do nothing. If you choose the image well, you will not have to bother with the
fact that it will not be resized in IE8 and lower. This does not apply to all
situations.

Detect properties and supply the browser with alternative styles using
Modernizr: `.no-backgroundsize .element { … }`.

Use the `filter` parameter. This can be only used if the background image has
equal aspect ratio and if it’s the same size or larger than the parent element:

```css
.element {
  background-size: contain;
  filter: progid:DXImageTransform.Microsoft.AlphaImageLoader(
    src='images/image.jpg', sizingMethod='scale');
}
```

Use a polyfill. Just be careful - the polyfill is using `.htc` files so it may
lower the website’s performance. See
[github.com/louisremi/background-size-polyfill](https://github.com/louisremi/background-size-polyfill).
