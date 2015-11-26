CSS3 Flexbox – A Layout Made of Flexible Boxes
==============================================

What is Flexbox?
----------------

It is an approach to layout creation, aligning elements and distributing extra
space.

*Flex* stands for *flexible*, *adaptive*. Flexboxes are thus *flexible* elements
of the layout. One of the main advantages of flexbox is the ability to fill
extra space without the need of using Javascript.

### The Very Basics Shown in an Example

Lets imagine a simple 3-column layout:

```css
<div class="container">
  <p class="mandatory-1">One</p>
  <p class="content">Two<br/>…<br/>…</p>
  <p class="mandatory-2">Three </p>
</div>
```

The simpler the HTML the stricter design requirements there are. And you know
what? Let's see how to meet them using flexbox.

1.  **Equal column height.** That's right - even if one column has more content
    than the remaining ones. This is easy. All you need to do is add `.container
    { display: flex; }` to the parent element.

2.  **One fifth grid**. The first and third column should take up one fifth –
    `.mandatory-1, .mandatory-2 { flex: 1; }`. The second column should take up
    three fifths – `.content { flex: 3 }`. Did you notice that we do not operate
    with percentage or that we do not calculate the dimensions again when adding
    a new column?

3.  **Change element order on lower resolution screens.** Simply add the
    `.content { order: -1; }` declaration to your media query and the `.content`
    column will appear first. That's a real stunner for responsive design, isn't
    it?

Hurry up and try an example at CodePen – <http://cdpn.io/e/LhGuD>.

It is nice, isn't it? However, a "grouch" would say that CSS has already learned
what we could do with [table
layout](http://www.jakpsatweb.cz/tabulky-design.html) back in 2001. Sure, but
he would be just "somewhat" right. Flexbox can do much (*much!*) more than just
tables.

### Why Do We Need Flexbox?

Let me ask you a question first. How do we handle layouts in CSS?

Using floats, inline-blocks, absolute positioning or `display: table`. And do
you know what these terms all have in common? Not a single one of them was meant
for today's layouts. Yes, flexbox is truly the first CSS layout tool. And our
grouch might add: "The first one in twenty years…".

Floats, tables and all other *layout techniques soon to be dead* will still come
in handy over the next few years. Every member of this "layout tools family" has
more or less disadvantages when it comes to creating layouts. They come from
specifications that did not involve today's layout.

### Component Layouts

It is worth mentioning that flexbox is designed for component layouts inside
pages. To be precise: for navigations, forms, paginations, etc.

When dealing with full page layouts, its is better to use a CSS3 Grid Layout
which unfortunately has little browser support. However, using flexbox for full
page layouts is possible - you just need to watch out for slow devices or
internet connections where it is not going to render optimally. See
<http://jakearchibald.com/2014/dont-use-flexbox-for-page-layout/>

Let's Get Down To Basic Terms — Flex Container and Flex Item, Main Axis and Cross Axis
--------------------------------------------------------------------------------------

Flexbox contains two inseparable types of elements – flex container and flex
item. A flex item is a direct child of a container.

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

In the following text, you will have to pay attention to axes so let's
illustrate this in a simple scheme:

![flexbox scheme](content/schemes/flexbox-schema.jpg)

-   flex container – parent element
-   flex item – all direct children of a flex container
-   main axis – horizontal is default but it can be changed
-   cross axis – perpendicular to the main-axis, so it is similar to the main
    axis when default
-   main size – width is default but is dependent on the main axis setting
-   cross size – width is default
