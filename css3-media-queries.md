CSS3 Media Queries – Conditional Directives for Different Media Types
=====================================================================

The principle is simple. A certain part of CSS declarations will apply only if
Media Queries conditions have been met.

Together with fluid layout and fluid media, media queries form one of the three
pillars of classic responsive web design.

You might know CSS2 media type conditions such as — `@media print { … }`. CSS3
Media Queries extend this idea with media types.

Syntax
------

You can insert media queries directly into a CSS file:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
@media (_conditions_) {
    /* css code which will apply
if _conditions_are_met_ */
}
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Or into HTML where reference to a CSS file is:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
<link rel="stylesheet"
href="mobile.css" media="max-width: 480px">
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

### Minimal/maximal Height/width

A typical media query looks like this:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
@media (max-width: 480px) {
    .container {
        width: auto
    }
}
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The declaration of `.container` will apply if the viewport width (visible area
of a web page) does not exceed 480 pixels.

Alternatively, you can detect the width of the display screen: `@media
(max-device-width: 480px)`. Unlike using `max-width`, window resize will not
affect it.

Now, let's get back to the remaining queries based on viewport dimensions. It is
not hard to tell what they will look like:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
@media (min-width: 100px) { … }
@media (max-height: 100px) { … }
@media (min-height: 100px) { … }
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

You can try a live example of Media Queries here:
[cdpn.io/e/aCBAr](<http://cdpn.io/e/aCBAr>).

### Logical Operators

You can compose media queries using the `and` operator and thus layer and
combine them with media types:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
@media screen and (min-width: 400px)
and (max-height: 600px) { … }
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The `or` operator can be substituted with a comma:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
@media (max-width: 400px), print { … }
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The `not` operator is used to negate the result.

### Additional Properties for Querying

**Detection of high-resolution displays** such as Retina, Amoled and other:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
@media
    (-webkit-min-device-pixel-ratio: 1.5),
    (min-resolution: 144dpi) {
        background-image: url(image_hd.png);
    }
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

If the device-pixel-ratio is 1.5 or greater, the `image_hd.png` will be loaded.

There are numerous pixel aspect ratios available (1.25, 1.5, 2, 3, 4).
Therefore, I recommend to use a SVG vector format instead of bitmap images where
possible.

**Detecting device orientation.** Is the orientation portrait or landscape?

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
@media (orientation: portrait) { ... }
@media (orientation: landscape) { ... }
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

**Screen aspect ratio condition**

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
@media screen and (device-aspect-ratio: 16/9) { ... }
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

So these were the most common types of queries. However, there are [a lot
more](<http://www.opera.com/docs/specs/presto26/css/mediaqueries/>).

Browser Support
---------------

IE8 does not support even the simplest media query. Fortunately, there are
several strategies how to handle it and not be discouraged. But for those
strategies, responsive web design could not have come to life in the first
place. So if you got scared, pull yourself together and move on.

Below are three strategies how to deal with the fact that IE8 does not support
Media Queries.

1.  Use a [Respond.js](<https://github.com/scottjehl/Respond>) polyfill. It is
    well tested and fast enough. Plus it is used by a very popular framework -
    Bootstrap.

2.  Declare CSS so IE 8's shortcomings are not a problem. Declare CSS for
    desktop by default and then put declarations for smaller displays into media
    queries.

3.  Or make use of a CSS preprocessor and either use body classes or compile an
    extra file for handling older Internet Explorers.
