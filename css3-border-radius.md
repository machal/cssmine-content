CSS3 Border Radius
==================

Rendering rounded and elliptical corners...

Syntax
------

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
border-radius:
    _top_right_radius_
    _bottom_right_radius_
    _bottom_left_radius_
    _top_left_radius_
    (/ _elliptical_variations_);
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Evenly rounded corners with a 10 pixel radius can be pulled off like this:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
border-radius: 10px;
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

We can also round corners using a percentage of the width of the element or
using other units that are available in CSS. However, you can round **each
corner separately**. You always start from the top left corner and proceed
clockwise:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
border-radius: 15% 15% 0 0;
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

If you add a forward slash, the element will have an **elliptical shape**, not a
circle shape. The first corner will be rounded in an ellipse with a vertical
radius of 15% and horizontal radius of 30%:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
border-radius: 15% 15% 0 0 / 30% 15% 0 0;
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The following scheme shows how the ellipse rounding works in practice:

It is good to know that `border-radius` is in fact a shorthand property for
setting four `border-radius` properties **individually**:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
border-top-left-radius: 4em;
border-top-right-radius: 4em;
border-bottom-right-radius: 4em;
border-bottom-left-radius: 4em;
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

See a live border-radius example at [cdpn.io/e/EljFa](<http://cdpn.io/e/EljFa>).

Tips and Tricks
---------------

How to create **rounded avatars** using `border-radius`? See
[trentwalton.com/2010/08/03/css3-border-radius-rounded-avatars/](<http://trentwalton.com/2010/08/03/css3-border-radius-rounded-avatars/>)

How to tackle **tables with rounded corners**? When dealing with tables that
have the `border-collapse: collapse` property or a parent element with an image
in it, it is necessary to apply `overflow: hidden`. See more at
[cdpn.io/e/jpdFm](<http://cdpn.io/e/jpdFm>)

Browser Support
---------------

There is absolutely no problem in modern browsers. If you need rounded corners
in IE8, just use [css3pie.com](<http://css3pie.com/>) but watch out - it is
going to slow your web site down.

Therefore, I strongly recommend a zero fallback strategy. As a result, users
with older browsers simply will not see rounded corners. And what the eye
doesn't see, the heart doesn't grieve over.

If the background color leaks outside of a rounded corner in some browsers, just
add `background-clip: padding-box`. See
[tumble.sneak.co.nz/post/928998513/fixing-the-background-bleed](<http://tumble.sneak.co.nz/post/928998513/fixing-the-background-bleed>)

MSIE9 supports `border-radius`, however it is not possible to combine it with
the `filter` property that is widely used for color transitions. It can be
solved by setting a `hidden` value for both the `border-radius` and `overflow`
properties of a parent element.
