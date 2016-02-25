CSS3 Media Queries – Conditional Directives for Different Media Types
=====================================================================

The principle is simple: a certain number of CSS declarations will apply only if
Media Queries conditions have been met.

Together with fluid layout and fluid media, Media Queries form the three pillars
of classic responsive web design.

You might know CSS2 media type conditions, such as: `@media print { … }`. CSS3
Media Queries extend this idea with media types.

Syntax
------

You can insert Media Queries directly into a CSS file:

```css
@media (_conditions_) {
    /* css code which will apply
if _conditions_are_met_ */
}
```


Or into HTML where the reference to a CSS file is:

```html
<link rel="stylesheet"
  href="mobile.css" media="max-width: 480px">
```


### Minimal/Maximal Height/Width

A typical Media Query looks like this:

```css
@media (max-width: 480px) {
 .container {
    width: auto
  }
}
```

The declaration of `.container` will apply if the viewport width (the visible
area of a web page) does not exceed 480 pixels.

Alternatively, you can detect the width of the display screen using: `@media
(max-device-width: 480px)`. Unlike using `max-width`, window resize will not
affect it.

Now, let's get back to the remaining queries based on viewport dimensions. It is
not hard to tell what they will look like:

```css
@media (min-width: 100px) { … }
@media (max-height: 100px) { … }
@media (min-height: 100px) { … }
```


You can try out a live example of Media Queries here:
[cdpn.io/e/aCBAr](http://cdpn.io/e/aCBAr).

### Logical Operators

You can compose Media Queries using the `and` operator and thus layer and
combine them with media types:

```css
@media screen and (min-width: 400px)
and (max-height: 600px) { … }
```

The `or` operator can be substituted with a comma:

```css
@media (max-width: 400px), print { … }
```

The `not` operator is used to negate the result.

### Additional Properties for Querying

**Detection of high-resolution displays** such as Retina, Amoled and other:

```css
@media
    (-webkit-min-device-pixel-ratio: 1.5),
    (min-resolution: 144dpi) {
        background-image: url(image_hd.png);
    }
```


If the device-pixel-ratio is 1.5 or greater, `image_hd.png` will be loaded.

There are numerous pixel aspect ratios available (1.25, 1.5, 2, 3, 4).
Therefore, I recommend using an SVG vector format instead of bitmap images where
possible.

**Detecting device orientation.** Is the orientation portrait or landscape?

```css
@media (orientation: portrait) { ... }
@media (orientation: landscape) { ... }
```

**Screen aspect ratio condition**

```css
@media screen and (device-aspect-ratio: 16/9) { ... }
```

These are the most common types of queries; however, there are [a lot
more](http://www.opera.com/docs/specs/presto26/css/mediaqueries/) of them.

Browser Support
---------------

IE8 does not support even the simplest Media Query. Fortunately, there are
several strategies for handling them without becoming discouraged. But for those
strategies, responsive web design could never have come to life in the first
place. So if you are scared now, pull yourself together and let's move on.

Below are three strategies for dealing with the fact that IE8 does not support
Media Queries.

1.  Use a [Respond.js](https://github.com/scottjehl/Respond) polyfill. This is
    well tested and fast enough. Plus, it is used by a very popular framework -
    Bootstrap.
2.  Declare CSS so IE8's shortcomings are not a problem. Declare CSS for desktop
    by default and then put the declarations for smaller displays into Media
    Queries.
3.  Make use of a CSS preprocessor and then use body classes or compile an extra
    file for handling older Internet Explorers.
