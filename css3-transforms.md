CSS3 Transforms – Object Transformations
========================================

It can be a transformation of a shape, position or element size.

There are four available functions: skew, rotate, translate and scale:

```css
/* Skew */
.skew {
  transform: skew(-15deg);
}

/* Rotate */
.rotate {
  transform: rotate(-15deg);
}

/* Translate */
.translate {
  transform: translate(0, 50%);
}

/* Scale */
.scale {
    transform: scale(1.5);
}
```

Try it at <http://cdpn.io/e/wxoil>.

All four functions transform an element around a corresponding axis. For example
`skewX()`, `skewY()`.

Combination of Transformations
------------------------------

Remember that combinations of transformations are not separated by a comma:

```css
transform: scale(1.5) skew(-15deg);
```

Transformation Origin
---------------------

It is sets the point of origin of a transformation. By default, the origin is in
the center of an element: `transform-origin: center center`. If we set the
origin to the top left corner, it will cause the element to scale from that
point:

```css
.scale-2 {
  transform: scale(1.5);
  transform-origin: top left;
}
```

See more at [cdpn.io/e/brBgk](<http://cdpn.io/e/brBgk>)

Browser Support
---------------

IE10+. For older browsers, you will probably need feature detection using
Modernizr and then come up with an alternative solution. Basic 2D
transformations can be carried away in older Internet Explorers using a
proprietary
[filter](<http://msdn.microsoft.com/en-us/library/ms533014%28VS.85%29.aspx>)
function. Also, there is a [smart
converter](<ttp://www.useragentman.com/IETransformsTranslator/>) for CSS3 to
filter conversion.
