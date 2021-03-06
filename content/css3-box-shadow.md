CSS3 Box Shadow
===============

This is a typical shadow attached to an element. This is usually under the
element but it can also be inside it or create a relief effect.

Syntax
------

```css
box-shadow:
  (inset)
  _horizontal_offset_
  _vertical_offset_
  (_blur_)
  (_spread_)
  _color_,
  (_other_shadows_);
```

The basic kind of shadow can be created in a jiffy. The first number indicates
the **horizontal offset, the second the vertical one** - a positive value
offsets the shadow down or right, a negative one up or left. The third value is
color and believe it or not, the best practice is to use a semi-transparent
[RGBa color](css3-rgba.md). Let’s show this using several examples.

```css
box-shadow: 5px 5px rgba(0, 0, 0, .5);
```

If we add another number, the browser will indicate that you want to **blur**
the shadow:

```css
box-shadow: 5px 5px 10px rgba(0, 0, 0, .5);
```

One more number and you will define the **spread distance**:

```css
box-shadow: 5px 5px 10px 10px rgba(0, 0, 0, .5);
```


The key word **inset** changes the shadow from outer to inner:

```css
box-shadow: 5px 5px 10px 10px rgba(0, 0, 0, .5);
```

You can also create **multiple shadows** by dividing the values with a comma.
The first shadow is the top one:

```css
box-shadow: 5px 5px 10px 10px rgba(0, 0, 0, .5),
  inset 5px 5px 10px 10px rgba(0, 0, 0, .5);
```

You can see a live example at [cdpn.io/e/lAoDv](http://cdpn.io/e/lAoDv).

Tips and Tricks
---------------

### Shadow on One Side

If we want to create a shadow on one side only, simply set the horizontal shadow
to `0`. However, bear in mind that thanks to using blur, the shadow will be
leaking from the top and bottom:

```css
box-shadow: 5px 0 5px -2px rgba(0,0,0,.5);
```

See a live example at [cdpn.io/e/JnGyb](http://cdpn.io/e/JnGyb).

### Shadow as a Copy of an Object

Drawing the Microsoft logo using a shadow may be rather impractical but it also
demonstrates the power of using multiple shadows without blurring. See an
example at [cdpn.io/e/qJuzw](http://cdpn.io/e/qJuzw).

You can also combine blurred and sharp shadows:
[dabblet.com/gist/2043600](http://dabblet.com/gist/2043600).

Browser Support
---------------

IE9+. There is almost no problem in any modern browser:
[caniuse.com/box-shadow](http://caniuse.com/box-shadow)

### Older Webkit Browsers Sometimes Ignore the Spread

A slight problem in older webkit browsers is that they ignore the null value of
the spread if a value for blur is missing. Therefore, the following notation
won’t work in iOS6 Safari or Android Browser 2.3:

```css
box-shadow: 5px 5px 0 rgba(0, 0, 0, .5);
```

This one, on the other hand, will:

```css
box-shadow: 5px 5px 10px rgba(0, 0, 0, .5);
```

See a live example at [cdpn.io/e/FGtbu](http://cdpn.io/e/FGtbu).

### Internet Explorer 8

In IE8, a box shadow can be rendered using the `filter` proprietary property.
Example:

```css
filter: progid:DXImageTransform.Microsoft.Shadow(color='#cccccc', Direction=145, Strength=3);
```

However, not all types of shadows can be substituted like this.

In older versions of Internet Explorer, a shadow can be rendered using a
[css3pie.com](http://css3pie.com/) polyfill but usually you can get away with
this using the zero fallback strategy.
