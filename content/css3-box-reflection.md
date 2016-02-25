Box Reflection
==============

The browser will render a reflection of the element under or next to it.

Syntax
------

The syntax is based on the Webkit core:

```css
-webkit-box-reflect:
  _reflection_direction
  _offset_
  _mask_;
```

### Direction of the Reflection

This is a required value with four possible choices: `above`, `below`, `left` or
`right`.

```css
-webkit-box-reflect: below;
```

### Offset

This defines the distance of a reflection from the original object, using
standard CSS units – `px`, `em` and others.

```css
-webkit-box-reflect: below 5px;
```

### Mask

A mask defines the reflection overlay effect. A [CSS
gradient](css3-gradients.md) is a commonly used tool for achieving the mirror
effect: however, it can also be done using an image. The black area of a mask is
visible, the transparent one is hidden.

```css
-webkit-box-reflect:
  below 5px linear-gradient(to bottom, transparent, black);
```

Take a look at a live example at [cdpn.io/e/CLEhF](http://cdpn.io/e/CLEhF).

Browser Support
---------------

Box reflection is supported only by Webkit browsers. Nowdays, it works in all
versions of Safari and even in Android Browser. It works even in Chrome which
has its own Blink core. See
[caniuse.com/box-reflect](http://caniuse.com/box-reflect)

In Firefox, we can achieve a reflection effect by using the `-moz-element()`
property. See
[lea.verou.me/2011/06/css-reflections-for-firefox-with-moz-element-and-svg-masks/](http://lea.verou.me/2011/06/css-reflections-for-firefox-with-moz-element-and-svg-masks/)

This property is not reliable when dealing with a big target group, however, it
might come in handy for internal apps with a limited target audience.
