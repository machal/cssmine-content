Flexbox: Browser Support
========================

Browser support is not bad. At the time of this writing, the level of support
was 92–95% when using reasonable fallbacks for older browsers, so there is
no reason not to use flexbox right away.

### Three Types of Syntax in Modern Browsers

A well-configured Autoprefixer, which we mentioned at the beginning of this
e-book, will definitely guarantee full modern browser compatibility. So read on
if you are into details.

There are three types of flexbox syntax in modern browsers.

-   **New syntax:** `display: flex` and other properties shown in this e-book.
    This is supported by the latest versions of all browsers, including IE11 and
    Opera Mini.
-   **Tweener syntax from 2012:** `display: flexbox`. Nowdays required just by
    IE10.
-   **Legacy syntax from 2009:** Wherever you see `display: box` or
    `-webkit-display: box`. Webkit prior to version 20, i.e. iOS6 or older
    Androids.

### How to Handle Unsupported Browsers?

It applies to IE9 and older. Just take a look at your project stats to see how
many visitors use these older browsers and address the issue accordingly:

#### Zero fallback – i.e., We Do Not Care About Support

It is good to realize and test in practice what it truly means “not to bother
with flex box support in older browsers”.

You can see this in the following picture where the form makes use of flexbox.
In Safari, the form is displayed as planned. In IE8, the text input will not
fill the whole area and the “Other” caption will not grow in size as font size
increases:

![Fallback for IE8](dist/images/original/flexbox-ie8-fallback.jpg)

This is an example we already have already seen:
[cdpn.io/e/jEJbmg](http://cdpn.io/e/jEJbmg).

The form is still functional, yet some features are not user-friendly. Sure, why
not? A layout can also be taken as enhanced user experience (meaning it does not
apply to rounded corners only):

![Layout as an enhancement](dist/images/original/flexbox-layout-as-enhancement.jpg)

#### Feature Detection and an Alternative Solution

On the other hand, zero fallback can’t be used when aligning a box with the
center of the page. If it is necessary to keep a similar look, we would need to
use an alternative solution using CSS or Javascript.

As mentioned in the first chapter, the Modernizr feature detection using the
`.no-flexbox` class would be a life saver.

The solution would look like this:

```css
.vertical-centered {
  /* Flexbox centering */
}

.no-flexbox .vertical-centered {
  /* Centering without flexbox */
}
```


This way, you can make an alternative layout using `display:
table|table-row|table-cell`.

#### Defined Fallback

Flexbox is just a new value of the `display` property, making it very useful if
we want the former `inline` or `inline-block` elements to stack on top of each
other. If a browser does not support flexbox, the elements will simply stack on
top of each other the same way they do in mobile device browsers.

```css
.box {
  display: block;
  display: flexbox;
}
```

A `float` fallback is very simple to use because it will not apply to flex box
items in modern browsers:

```css
.container {
   display: flexbox;
}

.box {
  display: block;
  float: left;
}
```


#### Flexbugs – The Most Common Bugs of Browsers

As you may have noticed, flexbox is a relatively new and complex standard which
is exposing a number of minor bugs in browsers.

Apart from looking up bugs at Google or StackOverflow, you can take a look at
the **flexbugs** project. This Phillip Walton project is gathering, documenting
and finding solutions for the most common bugs.

See [github.com/philipwalton/flexbugs](https://github.com/philipwalton/flexbugs)
