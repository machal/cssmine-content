CSS3 Box Sizing – a Way of Calculating the Box Size
===================================================

It is a change in calculating the width and height of an element or the
box-model.

You will learn why developers who make fluid layouts just love the `box-sizing:
border-box` property. And you will also learn why people who hate math love it.
Just go on.

Syntax
------

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
box-sizing: content-box | border-box | padding-box;
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Do you remember the [traditional
box-model](<http://en.wikipedia.org/wiki/Internet_Explorer_box_model_bug>) value
that IE6 and older versions used to handle the sizing of elements?

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
The width or height of an element = actual visible width or height of the content + padding + border.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Are you getting it? This is `border-box` **box-model**.

In contrast, all other modern browsers use the `content-box` value **or the „W3C
box-model“**. And you know the drill:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
The width or height of an element = actual visible width or height of the content
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

This is the initial value of the `box-sizing` property which we can – thankfully
– change.

Just for the record: let's explain how the width and height of an element is
calculated when using the `box-sizing: padding-box` declaration. It is in fact a
`border-box` value where the width of the `border` property is not added in the
calculation.

Good, but how can we make use of it? Let's take a look at a few scenarios.

Examples of Use
---------------

### `* { box-sizing: border-box }`

Some may use the box-sizing property if the W3C box model is hard to tackle. The
W3C box model is also considered to be counterintuitive by the vast majority of
developers, and therefore they let browsers calculate all sizes using the
border-box value. A similar approach can be found in modern front-end frameworks
such as Bootstrap or Foundation.

### Fluid Layout

This property is vastly used in responsive web design, especially when working
with layouts that are percentage based. Just imagine navigation with more than 5
items and each item being 20% of the width. Plus the item separator is done
using a fixed with border:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
.nav li {
    width: 20%;
    display: inline-block;
    border-left: .25em solid #fff;
}
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Unfortunately, when using this notation, the fifth navigation item will break to
the next line. All we need to do is tell the browser that it would be a good
idea to calculate the width of the navigation items using the `box-sizing:
border-box` property:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
.nav li {
    box-sizing: border-box;
    width: 20%;
    display: inline-block;
    border-left: .25em solid #fff;
}
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

See a live example at [cdpn.io/e/FeLkJ](<http://cdpn.io/e/FeLkJ>).

### Changing the Size of Form Fields

The `box-sizing` property is very handy when it comes to unifying the way of
calculating width and height of form fields. Depending on the browser, some of
the fields are handled using the `content-box` property, some using the
`border-box` property (i.e. `input type=„submit“` vs `select`). If you want to
make sure that all form elements in your design have the same height, just
declare `box-sizing: border-box` before you even start to think about styling
them. A live example of form fields can be found at
[cdpn.io/e/iBquK](<http://cdpn.io/e/iBquK>).

Browser Support
---------------

IE7+ and all modern browsers. If you previously did not know about this
property, you will be surprised how well it is supported:
[caniuse.com/box-sizing](<http://caniuse.com/box-sizing>).

On the other hand, it is good to know that the not-so-common `padding-box`
property is supported by Firefox only.
