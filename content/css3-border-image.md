CSS3 Border Image – Custom Borders
==================================

This is a way which allows you to create custom boxes around elements instead of
using the native ones.

Take any image that contains a border and tell the browser how to slice it. Then
there is the "magic" part - the border will adapt to the width and height of the
element, whatever it may be.

Syntax
------

```css
border-image:
    _image_source_
    _slice_size_
    _border_width_
    _slice_start_
    _repeat_
```

### Image Source

This is the only required property, written as `border-image-source: url(…)`.

### Slice Sizes

Thanks to this value we can slice the source image so the browser knows where
all four cut-outs for all four corners are. Plus the browser will know where the
cut-outs for the horizontal and vertical sides are.

The value consists of one, two or four numbers. Two numbers represent the
horizontal and vertical slice and four numbers represent the top, right, bottom
and left slices. The value can be defined in pixels or as percentage of the
source image size. The default value is `border-image-slice: 100%`.

If the `fill` key word is used, the browser will apply the center part of the
image to the element's background.

![Slice Sizes within border-image](dist/images/original/border-image.svg)

### Border Width

The `border-image-width` property defines the border width in pixels or as a
percentage. It is very similar to `border-width`.

If the `auto` value is applied, the width is calculated from the slice size.

### Start of the Slice

The value of the `border-image-outset` property defines how far the image border
extends past the element. It is calculated as if the element had a [box-sizing:
border-box](css3-box-sizing.md) property.

### Repeating

How will the browser work with the vertical and horizontal side of the image
border if the border has different size than the source image? We can set this
by using the `border-image-repeat` property. There are four values available:

-   `stretch` – the image will stretch to fill the border
-   `repeat` – the image will not repeat
-   `round` – if the area is not filled by an integer number of repetitions,
    each repetition will stretch to fill the area
-   `space` – if the area is not filled by an integer number of repetitions, the
    empty area is evenly distributed among all repetitions (space is added to
    each repetition)

Remember that it is possible to set various values for the horizontal and
vertical parts of the border. See an example:

```css
border-image-repeat: stretch repeat;
```

Useful Tips
-----------

[border-image.com](http://border-image.com/) - a very nice generator which
will make your life easier especially when looking for size of the slices.

-   Attention! According to the latest specification, the `border-image`
    property will not work if you forget to declare `border-style` and
    `border-width` properties.

Browser Support
---------------

IE11+. Older browsers can be tackled by a defined alternative and by feature
detection using Modernizr: `.no-borderimage .box { … }`. Or simply by using a
`border-color` fallback.

A Simple Example with a Color Gradient
--------------------------------------

[CSS gradients](css3-gradients.md) count as images, therefore you can use a
color gradient as a border.

But remember that you always have to define a native image border. First for
handling sizes, second for creating a fallback for browsers not supporting
`border-image`. So, for the sake of this example, let's create a 20 pixel border
around an element:

```css
border: 20px solid green;
```

And now, we will tell the browser that instead of a green color, we we will use
a color gradient:

```css
border-image-source:
  linear-gradient(lightgreen, darkgreen);
```

To our surprise, the browser will render the gradient in the corners of the
border only. The reason for that is the slice default value:
`border-image-slice: 100%`. It means the image will be used just in the four
corners. Therefore, we will set it so it corresponds with the width of our
border:

```css
border-image-slice: 20;
```

And that's it. You can try an example at
[codepen.io/machal/pen/zdyIJ](http://codepen.io/machal/pen/zdyIJ).

An Example with a Bitmap Image as a Background
----------------------------------------------

First, let's define the border sizes and a fallback for older browsers:

```css
border-color: green;
border-style: solid;
border-width: 21px 23px;
```

Now add a background image:

```css
border-image-source: url(border-image-source.png);
```

Then define the slices. In this source image, the horizontal border is 21 pixels
high and the vertical one is 23 pixels high.

```css
border-image-slice: 21 23;
```

Last, it is necessary to tell the browser that side slices need to be repeated
if the size of the element increases:

```css
border-image-repeat: repeat;
```

Now, let's try a shorthand notation of the last three declarations:

```css
border-image:
  url(border-image-source.png) 21 23 repeat;
```

Done. You can try an example at
[codepen.io/machal/pen/DLkjm](http://codepen.io/machal/pen/DLkjm).
