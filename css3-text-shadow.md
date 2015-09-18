CSS3 Text Shadow
================

Textu shadowing effect.

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
text-shadow:
    _horizontal_distance_
    _vertical_distance_
    (_blur_)
    _colour_,
    (_other_shadows_);
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Let's take a look at a live example at
[cdpn.io/e/aDLCl](<http://cdpn.io/e/aDLCl>).

the `text-shadow` property has a twin — [box-shadow](<css3-box-shadow.md>). Go
to the [box-shadow] page to see a detailed description of the syntax. It is very
similar.

Tip – you can use multiple text shadow values to create a [pseudo-3D
effect](<http://markdotto.com/playground/3d-text/>).

Browser support
---------------

IE10+. In older browsers, you can use a fallback without a shadow (preferred) or
simply create an IE8 version: by using Modernizr conditions or IE conditional
comments create a DropShadow (using a Microsoft filter).
