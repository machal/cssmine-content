CSS3 Multiple Backgrounds
=========================

How to layer multiple images or colors in one element?

In fact, multiple backgrounds are not a CSS property - just a new way of using
the existing `background` property.

And what is the syntax? Simply divide the layer using a comma:

```css
background:
  url('top_image.png'),
  url('center_image.png'),
  #ddccaa;
```

The image before the first comma will always be the top one.

If you do not use a `background` shorthand, the declaration of other background
image properties will also be divided by a comma:

```css
background-image:
  url('image.png'),
  url('next_image.png');
background-repeat:
  no-repeat,
  repeat;
```

Try it Yourself
---------------

Remember that an image can also be represented by a [CSS3
gradient](css3-gradients.md) with a semi-transparent background. You can make
use of this effect to cover the image even if you do not know the height of the
element:

```css
background:
  linear-gradient(180deg, transparent 0%, #333 100%),
  url('bg.jpg');
```

See a live example at [cdpn.io/e/lvKkC](http://cdpn.io/e/lvKkC).

Browser Support
---------------

IE9+. Be careful - the `background` property with multiple values is ignored if
the browser does not know how to handle it. Therefore, you always have to define
a fallback for older browsers such as IE8. See an example:

```css
background: #ddccaa;
background:
  url('top_image.png'),
  url('center_image.png'),
  #ddccaa;
```
