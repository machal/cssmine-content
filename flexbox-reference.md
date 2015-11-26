Flexbox Autopsy — Reference Guide
=================================

### What Is Good To Know

1.  `flex` is a new value of the `display` property. Therefore, we cannot apply
    properties such as `display: block`, `inline` or `inline-block` to the
    parent element or its children. Nor can we apply `float`, `clear` or
    `vertical-align`. To be precise, we can apply these properties, however they
    will not have any effect when displaying the web site in a browser without
    flexbox support. But it is useful when creating fallbacks for older
    browsers.

2.  In relation to the previous point, `margins` of adjacent items will not be
    collapsed, unlike using block elements.

3.  Element positioning (`position: absolute|relative|fixed`) can be applied
    when using flex items, unlike using the `float` property.

4.  When dealing with flex items, we can apply `visibility: collapse` the same
    way we would apply it when dealing with the `display: table-row` or
    `table-column` properties. An element will then take up space in the DOM,
    however it will not be visible.

5.  The direction of the main axis of a flex container is always based on the
    `writing-mode`. Therefore, if we created a layout of a Japanese page using
    flex box, all values would change their order.

Now let's dig into the "Reference Guide". We already know that there are two
types of flex elements – a flex container and a flex item. Therefore, we also
divide the properties according to the element types.

### Flex Container Properties

#### flex-direction – Direction of Flexible Items

This property will set the direction of the main flexbox axis.

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
flex-direction: row | row-reverse | column | column-reverse
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The default (`row`) value will place all flex items in a row. If you want to
make a vertical oriented layout, use the `column` value.

The order of items will correspond with the HTML order. If you want to reverse
the order, just use the `row-reverse` or `column-reverse` values. This will only
affect the visual rendering of the items, not the actual order - i.e. when
rendering a site or going through the navigation using `Tab`. Some of you might
have noticed that we can use this property when changing the order of list
items.

#### flex-wrap – Forcing Items to Break

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
flex-wrap: nowrap | wrap | wrap-reverse
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The default `nowrap` value tells us that all elements will stay on a single line
next to each other (or under each other when using `flex-direction: column`).

Then there is the `wrap` value. This value will wrap the items onto multiple
lines if the items' content can't fit into a single line. The last flex item on
the first line will break onto the next line and align under the first item.

The `wrap-reverse` value does the opposite - the last item will jump onto the
previous line and align over the first item.

#### flex-flow, A Shorthand for Flex-direction and Flex-wrap

Let's explain this in examples:

-   `flex-flow: row` – this is the default value. Items are placed in a single
    line and do not break.

-   `flex-flow: column wrap` – items are placed in a column and break.

We have explained the flex container properties. Now, let's explain flex items
as there is more to explain.

### Flex Item Properties

#### `flex-grow` – The Ability To Grow

How much can the item grow relative to the rest of the flexible items when there
is free space? When a user resizes the browser window for example? The items
will distribute the newly gained space beyond their default width. The values
can only be positive integers, defaulting in 0 which means that items will not
grow.

#### `flex-shrink` – The Ability To Shrink

How much will the flex item shrink relative to other items when there is not
enough space in the parent element? When a user resizes the browser window or a
new item is added for example. The values can only be positive integers,
defaulting in 1 which means that items will reduced their widths equally.

#### `flex-basis` – Default Item Size

This is the default width of the item (or height when using `flex-direction:
column`).

-   `auto` (default) – the width is defined by the content, similar to width:
    auto. The distribution of free space using the `flex-grow/flex-basis`
    properties will then affect just the extra space that is taken up by items
    beyond their initial size - the so called relative flex model.

-   `0` – size of the content is not an issue. The distribution of free space
    using the `flex-grow/flex-basis` properties will then affect the whole width
    of the item – absolute flex model.

-   Any CSS size, e.g. `100px`, `15em` or `50%`.

#### `flex` – Overall Item Flexibility

This is a shorthand for all properties that define the flexibility of an item –
`flex-grow`, `flex-shrink` and `flex-basis`. It sets the default element size
and tells us how an element can grow and shrink.

It is good to know that authors of the specification recommend to use the `flex`
shorthand rather than particular properties which it represents. This is because
the shorthand itself can set default values.

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
flex: <flex-grow> <flex-shrink> <flex-basis>
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The default value is:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
flex: 0 1 auto
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

-   `flex-grow: 0` – it will not expand to fill free space.

-   `flex-shrink: 1` – it will shrink just as all other items.

-   `flex-basis: auto` – it will take up space defined by its own content.

Let's assume you want your items to take up a minimum of `150px` and if there is
free space available, you want them to expand equally. On the other hand, if
there is not enough free space, you want them to shrink equally. You will do it
like this:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
flex: 1 1 150px
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

However, I think you are more likely to use pre-defined "intelligent" values:

-   `flex: auto`  
    It corresponds to `flex: 1 1 auto` and the items in question will become
    fully flexible, having the default width based on their contents. This is
    probably the most common case.

-   `flex: none`  
    It corresponds to `flex: 0 0 auto` and cancels the flexibility of the item.
    This is the second most common case.

-   `flex: initial`  
    It resets values to default, i.e. to `flex: 0 1 auto`. If there is not
    enough space, the items will shrink, however they will not expand beyond the
    size of their contents.

-   `flex: <positive-number>`  
    Watch out if you use a single number! The `flex: 1` declaration stands for
    `flex: 1 1 0` so the default size of the item and flex model will be
    changed. I have already mentioned it in the `flex-basis` property section.

![flex property](<images/flexbox-reference-flex.jpg>)

It is also good to know that flex items will never shrink below their minimum
content size. This size is defined by the length of the longest word or
fixed-size element – e.g. an image. It can be changed by setting the `min-width`
or `min-height` properties to a low value.

#### `order` – Change of the Order of Elements

The order of flex items corresponds with the HTML code, however we can change
that using the `order` property.

A change of the order affects the visual position of an element rendered by a
browser. It does not affect the actual order of items, i.e. when using a
document reader or going through the navigation using the `Tab` key.

The default value is `0` which basically means that it will correspond with the
"actual HTML order".

When using the following notation, you can make the third item visually appear
as the first one:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
.flex-item-third {
  order: -1;
}
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

But remember that you can't use `order` on other elements of the page except
direct children of the flex container.

### Aligning Flex Items

Now the next great thing about flexbox will play its part. We can finally align
layout elements both horizontally and vertically just by using CSS.

#### `margin` – Aligning Main Axis Items Within an Item

The `margin: auto` declaration works similar to block elements. When calculating
the size of flex items, the `auto` value does not matter. The free space is
equally distributed among all margins.

This allows you to set `margin-left: auto`, filling the left side of an element
with left margin and pinning the item to the right. You can use it instead of
the `float` property.

All other "alignment properties" have similar values, however they apply to
different sets of flex items or different container axes.

#### `justify-content` – Aligning Main Axis Items Within a Container

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
justify-content: flex-start | flex-end | center | space-between | space-around
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Let's apply the `justify-content` property to the flex container, saying how
flex items will be aligned along the main axis. The default value is
`flex-start`, aligning the items to the start of the main axis.

![justify-content](<images/flexbox-justify-content.jpg>)

#### `align-items` – Aligning Cross Axis Items Within a Container

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
align-items: stretch | flex-start | flex-end | center | baseline
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The `align-items` property can also be applied to the flex container. The
default value is `stretch` which stretches the item to the full width of the
cross axis.

![align-items](<images/flexbox-align-items.jpg>)

Be careful! The `stretch` value will not work if the items' size of the cross
axis is defined. In other words, if `height` is set, it will not work.

#### `align-self` – Aligning Cross Axis Items Within an Item

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
align-self: auto | flex-start | flex-end | center | baseline | stretch
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

This property is applied to each item so it is suitable for creating alignment
exceptions. The default value is `auto`.

#### Note: Baseline Alignment

Notice the alignment at the `baseline` of the first line. The item with the
greatest size between the baseline and the upper edge (the highest one) will be
pinned to the upper edge of the flex container. You can see it in the previous
image or at <http://cdpn.io/e/QwobXz>.

See that flexbox will not corrupt the upper pixel padding.

#### align-content – Aligning Main Axis Items Within a Multiple Line Container

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
align-content: stretch, flex-start, flex-end, center, space-between, space-around
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

And here is another alignment property. This time it applies only to flex
containers whose items are wrapped onto multiple lines.

![align-content.jpg](<images/flexbox-align-content.jpg>)

So, is that clear now? Ok, now let's move to browser support.
