Flexbox: What Is Good To Know
=============================

## 1. `flex` is a new value of the `display` property

Therefore, we cannot apply
properties such as `display: block`, `inline` or `inline-block` to the
parent element or its children. Nor can we apply `float`, `clear` or
`vertical-align`. To be precise, we can apply these properties, however they
will not have any effect when the website is displayed in a browser with
flexbox support. But it is useful when creating fallbacks for older
browsers.

## 2. Margins of flex items will not be collapsed

In relation to the previous point, margins of adjacent items will not be
collapsed, unlike when block elements are used.

## 3. Element positioning can be applied

Element positioning (`position: absolute|relative|fixed`) can be applied
when using flex items, unlike when the `float` property is used.

## 4. `visibility: collapse` will not be visible

When dealing with flex items, we can apply `visibility: collapse` the same
way we would apply it when dealing with the `display: table-row` or
`table-column` properties. An element will then take up space in the DOM,
however, it will not be visible.

## 5. The direction of the main axis is always based on the language

The direction of the main axis of a flex container is always based on the
`writing-mode`. Therefore, if we created a layout of a page in Japanese
using flex box, all values would change their order.

Now let’s dig into the “Reference Guide”. We already know that there are two
types of flex elements: a flex container and a flex item. Therefore, we divide
the properties according to the element type.
