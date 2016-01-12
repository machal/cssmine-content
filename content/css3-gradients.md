CSS3 Gradients
==============

A gradient lets you display the transition between two or more colors. Not long
ago, we had to use external images to achieve such an effect.

Linear Gradient
---------------

A uniform gradient from top to bottom can be achieved like this:

```css
background: linear-gradient(lightgreen, darkgreen);
```

### Gradient Axis

You can use **key words** representing either the direction of a gradient (`to
bottom right`, `to right`) or **angles**. An angle of 0° goes from bottom to
top, an angle of 90° from left to right and so forth clockwise. The default
gradient is 180° going from top to bottom (`180deg`).

For example, this gradient from light to dark green will go from the bottom left
corner to the top right:

```css
background:
  linear-gradient(45deg, lightgreen, darkgreen);
```

### Color-stops

You can define how colors are distributed along an axis. That is why we use
color-stops that are definable in standard CSS units (`%`, `px`, `em`…). These
are the same stops you may know from graphic editors but these are written in
code.

```css
background:
  linear-gradient(45deg, lightgreen, darkgreen 33%);
```

In this example, the dark green color-stop starts at in one third of the way
along of the gradient axis. You can see and try a live example at
[cdpn.io/e/CcdBf](http://cdpn.io/e/CcdBf).

### Colors

A color gradient can be defined between two or multiple colors. And remember
that you can use all color definitions including [rgba](css3-rgba.md) or
`transparent`.

```css
background:
  linear-gradient(to bottom right, transparent,
    lightgreen 25%, rgb(0, 127, 0) 50%);
```

This CSS code will render a color gradient from the top left corner to the
bottom right corner like this: a gradient from transparent color to light green
will take up one quarter of an element and a gradient from light to dark green
will take up the area from one quarter to one half of an element. This time we
used the RGB color model.

Circle Gradient
---------------

A simple circle (radial) gradient can be created like this:

```css
.box-1 {
    background:
      radial-gradient(lightgreen, darkgreen);
}
```

### Shape and Size

The default shape is a `circle` but it can be changed to an `ellipse`.

Right after the shape, you can define the size of the gradient. The first option
is to define the **size by the radius of the circle**. When using a circle, one
number will do, when using an ellipse, you will need two. The first number
indicates the height, the second one the width of the ellipse.

```css
.box-2 {
  background:
    radial-gradient(ellipse 50px 30px,
      lightgreen, darkgreen);
}
```

Comment: the current specification does not allow usage of percentage to define
circle size. See
[dev.w3.org/csswg/css-images-3/\#radial-size-circle](http://dev.w3.org/csswg/css-images-3/#radial-size-circle)

The second option is to define the **size using key words**:

-   `closest-side` – the gradient will meet the closest side of an element
-   `farthest-side` – the gradient will meet the farthest side of an element
    (opposite of closest-side)
-   `closest-corner` – the gradient will meet the closest corner of an element
-   `farthest-corner` – the gradient will meet the farthest corner of an element
    (opposite of closest-corner)

### Center Position

The center position of a radial gradient is similar to the `background-position`
property. You just need to add an `at` key word:

```css
.box-3 {
  background:
    radial-gradient(at top left, lightgreen, darkgreen);
}
```

### Color-stops

Color-stops work similarly to the linear gradient. In the example below, the
browser will render a color gradient from light green which will take up one
quarter of the element and a gradient from light to dark green which will take
up the area from one quarter to one half of the element. The rest of the circle
will be filled with dark green:

```css
.box-4 {
  background:
    radial-gradient(lightgreen 25%, darkgreen 50%);
}
```

And here is a live example which contains all four options of the radial
gradient: [cdpn.io/e/cdyfx](http://cdpn.io/e/cdyfx).

Repeating Gradients
-------------------

Repeating gradients are declared the same way as normal gradients except we will
use the `repeating-linear-gradient()` or `repeating-radial-gradient()`
functions. Unlike normal gradients, the browser will not render a color when it
hits the last color-stop but it will repeat the defined gradient instead.

```css
.repeating-linear {
  background:
    repeating-linear-gradient(to bottom right,
      transparent, transparent 10%, green 10%, green 20%);
}
```

In this example we will outline a colored “zebra” using transparent color and
green.

Also note that we have defined a “sharp” gradient by using adjacent color-stops
(`transparent 10%, green 10%`). In other words, the neighboring colors will be
displayed without any blending.

Now, let's try a repeating radial gradient:

```css
.repeating-radial {
  background:
    repeating-radial-gradient(transparent,
      transparent 10%, green 10%, green 20%);
}
```

By defining repeating green stripes we are able to create a “target-like”
pattern. But watch out here! Some browsers such as Chrome or Firefox are
currently not able to render these complicated gradients smoothly. As a result,
the circle will be “pixelated”.

Browser Support
---------------

Radial gradients are not compatible with IE in versions 8 and 9 and Opera Mini.
Android Browser 2.3 is not able to render radial gradients at all and other
browsers still have issues. See
[caniuse.com/gradients](http://caniuse.com/gradients)

Therefore, do not forget to define a fallback. A gradient is considered a
background image so a fallback can be easily pulled off using a standard
background color:

```css
color: #fff;
background-color: green;
background-image:
  linear-gradient(lightgreen, darkgreen);
```

### Gradient, Formerly Known as the Thing From “prefix” Hell

Nowdays, gradients are not a big deal. However, browsers in various stages of
specification development have implemented various stages of the actual
specification, or use their own syntax, for that matter. So if you want to
support older versions of contemporary browsers, pay close attention to
vendor-prefixed variants.

### Older Syntax of WebKit-based Browsers

If you want to fully support older Chrome, Safari up to version 5, iOS Safari up
to version 4, Android Browser up to version 3 and a few other browsers, you have
to use an older syntax. Just watch out, the difference is not only in the prefix
but in the code as well. For example, the axis direction is defined by the side
or the corner where you want the gradient to start:

```css
background-image:
  -webkit-linear-gradient(top, lightgreen, green);
```

This is not likely to be a big deal for most web sites and you will settle for a
fallback using a background color. The latest versions of all browsers comply
with the W3C syntax we are using in our examples. And without prefixes, I might
add!

### `filter` in IE8 and IE9

This is very simple: two-color linear gradients can be achieved in older
Internet Explorers by using the proprietary filter property:

```css
-ms-filter:
  "progid:DXImageTransform.Microsoft.gradient(
    GradientType=0, startColorstr=#00ff00,
    endColorstr=#008800)";
```

In the `GradientType` parameter you can set a vertical (`0`) or horizontal (`1`)
direction of the gradient. Just bear in mind that filters can render slowly and
when using the `background-image` property, the filter will not apply.

Tips and Tricks
---------------

Remember that a gradient is actually the **background image of an element,** so
it can be used as a background image for list bullets (`list-style-image`) or as
a border image ([border-image](css3-border-image.md)).

The most common use of non trivial gradients is creating **graphic buttons**
through CSS. See
[cubiq.org/dropbox/cssgrad.html](http://cubiq.org/dropbox/cssgrad.html)

The following is almost a **scientific essay on gradients**: in this link, Ana
Tudor goes really deep into the topic and explains it using math. See
[hugogiraudel.com/2013/02/04/css-gradients/](http://hugogiraudel.com/2013/02/04/css-gradients/)

**ColorZilla Gradient Editor** will help you generate a gradient code applicable
to older browsers including a fallback for IE8 and IE9. See
[colorzilla.com/gradient-editor/](http://colorzilla.com/gradient-editor/)

Lea Verou has a nice gallery of **color patterns** created using CSS gradients
only. But think of it mainly as a showcase of options. See
[lea.verou.me/css3patterns](http://lea.verou.me/css3patterns)

The above-mentioned color patterns make use of the so called **sharp
transition,** which is not really a transition because there is a sharp edge
between colors. `background: linear-gradient(to bottom, transparent, lightgreen
33%, darkgreen 33%);` See [cdpn.io/e/licEd](http://cdpn.io/e/licEd)
