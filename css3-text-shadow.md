CSS3 Text Shadow
================

This is a text shadowing effect.

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
text-shadow:
    _horizontal_offset_
    _vertical_offset_
    (_blur_)
    _color_,
    (_other_shadows_);
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Let's take a look at a live example at
[cdpn.io/e/aDLCl](<http://cdpn.io/e/aDLCl>).

The `text-shadow` property has a twin — [box-shadow](<css3-box-shadow.md>). Go
to the [box-shadow] page to see a detailed description of the syntax. It is very
similar.

Tip – you can use multiple text shadow values to create a [pseudo-3D
effect](<http://markdotto.com/playground/3d-text/>).

Browser Support
---------------

IE10+. In older browsers, you can use a fallback without a shadow (preferred) or
simply create an IE8 version: by using Modernizr conditions or IE conditional
comments you can create a DropShadow (using a Microsoft filter).
