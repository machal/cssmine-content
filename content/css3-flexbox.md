CSS3 Flexbox – A Layout Made of Flexible Boxes
==============================================

What is Flexbox?
----------------

This is an approach to layout creation, alignment of elements and distribution
of extra space.

*Flex* stands for *flexible*, *adaptive*. Flexboxes are thus *flexible* elements
of the layout. One of the main advantages of flexbox is the ability to fill
extra space without the need to use Javascript.

### The Basics as Shown in an Example

Lets imagine a simple 3-column layout:

```css
<div class="container">
  <p class="mandatory-1">One</p>
  <p class="content">Two<br/>…<br/>…</p>
  <p class="mandatory-2">Three </p>
</div>
```


The simpler the HTML, the stricter the design requirements are. And you know
what? Let's see how to fulfill them using flexbox.

1.  **Equal column height.** That's right - even if one column has more content
    than the others. This is easy. All you need to do is add `.container {
    display: flex; }` to the parent element.
2.  **One-fifth grid**. The first and third column should take up one- fifth of
    the available space: `.mandatory-1, .mandatory-2 { flex: 1; }`. The second
    column should take up three fifths: `.content { flex: 3 }`. Did you notice
    that we do not use percentages and that we do not re-calculate the
    dimensions when adding a new column?
3.  **Change element order on lower resolution screens.** Simply add the
    `.content { order: -1; }` declaration to your [Media Query](css3-media-queries.md) and the `.content`
    column will appear first. That's a real stunner of responsive design, isn't
    it?

Hurry up and try an example at CodePen: [cdpn.io/e/LhGuD](http://cdpn.io/e/LhGuD).

This is nice, isn't it? However, a “grouch” would say that CSS had already
learned what we could do with table layout back in 2001. Sure, but that guy
would just be “somewhat” right. Flexbox can do much (*much!*) more than just
tables.

### Why Do We Need Flexbox?

Let me ask you a question first. How do we handle layouts in CSS?

Answer: by using floats, inline-blocks, absolute positioning and `display:
table`. And do you know what these terms all have in common? Not a single one of
them was meant for today's layouts. Yes, flexbox is truly the first CSS layout
tool. And our grouch might add: “The first one in twenty years!”.

Floats, tables and all other *layout techniques soon to be dead* will still come
in handy over the next few years. However, every member of this “layout tools
family” has some disadvantages when it comes to creating layouts. Those
disadvantages arise from specifications that did not anticipate today's layouts.

### Component Layouts

It is worth mentioning that flexbox is designed for component layouts inside
pages. I.e., to be precise, for navigations, forms, paginations, etc.

When dealing with full page layouts, its is better to use a CSS3 Grid Layout,
which unfortunately has little browser support. Nevertheless, using flexbox for
full page layouts is possible - you just need to watch out for slow devices or
internet connections where flexbox is not going to render optimally. See
[jakearchibald.com/2014/dont-use-flexbox-for-page-layout/](http://jakearchibald.com/2014/dont-use-flexbox-for-page-layout/)

Let's Get Down To Basic Terms - Flex Container and Flex Item, Main Axis and Cross Axis
--------------------------------------------------------------------------------------

Flexbox contains two inseparable types of elements: flex container and flex
item. A flex item is the direct child of a container.

```html
<ul class="flex-container">
  <li>…</li>
  <li>…</li>
</ul>
```

Flexbox can be defined just by using a flex container:

```css
.flex-container {
  display: flex;
}
```


All `<li>` items are thus flex items.

In the following text, you have to pay attention to axes, so let's illustrate
this with a simple scheme:

![flexbox scheme](dist/images/original/flexbox-schema.jpg)

-   flex container – parent element
-   flex item – all direct children of a flex container
-   main axis – horizontal is default, but it can be changed
-   cross axis – perpendicular to the main axis, vertical is default
-   main size – width is default but depends on the main axis setting
-   cross size – width is default
