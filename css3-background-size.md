CSS3 Background Size
====================

It specifies the size of background within an element.

Syntax
------

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
background-size:
    (cover/contain)
    _vertical_size_
    _horizontal_size_;
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The default value `background-size: auto auto` tells the browser to keep the
original size of the image.

As with other CSS properties, we can set the width and height simultaneously –
`background-size: auto`.

### `cover` and `contain`

The key word `cover` tells the browser to cover the whole area of an element.
`contain`, on the other hand, tells the browser to show the whole image.

`background-size: cover` is typically used to make sure an image covers the
whole website background – see an example at
[alistapart.com/d/supersize-that-background-please/index3.html](<http://alistapart.com/d/supersize-that-background-please/index3.html>)

`background-size: contain` is typically used when placing an icon as a
background of an element that resizes according to various screen resolutions or
if you want to use double or triple the size of an image due to high-resolution
displays. See
[studiopress.com/design/css-background-size-graphics.htm](<http://www.studiopress.com/design/css-background-size-graphics.htm>)

Tip: If you tend to work with icons this way, consider using a vector solution
(SVG or font icons) –
[css-tricks.com/icon-fonts-vs-svg/](<http://css-tricks.com/icon-fonts-vs-svg/>).

### Size in `px` or Percentage

The *vertical\_size* and *horizontal\_size* values can be defined in standard
CSS units – `px`, `em` and other.

When using percentage, the values are relative to the width or height of an
element to which the property is applied. For example: stretching a gradient
background to the full width and one half of the height of an element would look
like this:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
background: linear-gradient(to bottom, transparent, black) no-repeat bottom;
background-size: 100% 50%;
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Take a look at a live example at
[codepen.io/machal/pen/cmpjE](<http://codepen.io/machal/pen/cmpjE>).

And do not forget that background width or height is based on the setting of the
[background-origin](<css3-background-origin.md>) property. Thus, by default the
`padding-box` and `background-size` properties are calculated either from the
inner edge or from the content of an element.

### Multiple Background Images

If you are using [multiple background images](<css3-multiple-backgrounds.md>),
simply use a comma-separated list of values:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
background-size: 50% auto, auto;
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Browser Support
---------------

The `background-size` property is supported by all contemporary browsers except
IE8 –
see[caniuse.com/background-img-opts](<http://caniuse.com/background-img-opts>).

### `background-size` in IE8

There is no universal solution, however, depending on a particular situation,
you can choose from these four approaches:

Do nothing. If you choose the image well, you will not have to bother with the
fact that it will not be resized in IE8 and lower. This does not apply to all
situations.

Detect properties and supply the browser with alternative styles using Modernizr
– `.no-backgroundsize .element { … }`.

Use the `filter` parameter. It can be only used if the background image has the
same aspect ratio and if it is the same size or larger than the parent element:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
.element {
    background-size: contain;
    filter: progid:DXImageTransform.Microsoft.AlphaImageLoader(
        src='images/image.jpg',
        sizingMethod='scale');
}
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Use a polyfill. Just be careful - the polyfill is using `.htc` files so it may
lower the web site performace – see
[github.com/louisremi/background-size-polyfill](<https://github.com/louisremi/background-size-polyfill>).
