CSS3 Background Origin – Background Image Start
===============================================

This property determines where to position the axis for calculating sizes and
positions of other properties, such as
[background-size](css3-background-size.md) or `background-position`, within a
particular element:

-   `content-box` – starts from the element content
-   `padding-box` (default) – starts from the element padding edge
-   `border-box` – starts from the element padding edge but counts in the
    element `border` as well

Tip: The differences among the `content-box`, `padding-box` and `border-box`
values are illustrated in the [box-sizing](css3-box-sizing.md) section of this
e-book.

Caution! The `background-origin` property is ignored by the browser if the
`background-attachment: fixed` declaration is used.

Background Clip vs Background Origin
------------------------------------

Everyone gets confused by this so let's shed some light on it:

[Background Clip](css3-background-clip.md) determines whether the background
color or image is visible under a border (`border-box`) or only around the
content only (`content-box`).

Background Origin does not do anything on its own - it just defines an area
where other properties apply (e.g. [background-size](css3-background-size.md)
or `background-position`).

IE8
---

Again, there is no support for these properties in IE8. See
[caniuse.com/background-origin](http://caniuse.com/background-origin).

Neither polyfills nor the `filter` property workaround are available for this
property. The only thing to do is to ignore this property in IE8 or detect it
and come up with an alternative solution for older browsers.
