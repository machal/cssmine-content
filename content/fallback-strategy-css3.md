A Dinosaur-resistant CSS3 Technical Solution
============================================

There are five available strategies: zero or defined fallback, feature detection
or polyfills, and a special category of a so called generated fallback.

1) Zero Fallback
----------------

Number of fallback characters: zero. You simply do not write any alternative
code - provided you know exactly what you are doing.

Zero fallback makes use of smart HTML and CSS features - ignoring the unknown.
Browsers have always processed both languages in the following way: if they
encounter a tag, attribute, property or value they do not recognize, they simply
ignore it and continue rendering the code.

```css
.box {
  color: red;
  transition: .5s;
}

.box:hover {
  color: darkred;
}
```

In this example, we do not worry about the fact that older browsers do not
render transitions. The transition’s only purpose is to enhance the user
experience in modern browsers.

If, however, a transition carries information (e.g. a file upload indication),
we will have to provide a way for older browsers to understand it.

Therefore, the zero fallback provides a solution for getting away with
animations, rounded corners, shadows, custom fonts and many other CSS3
properties in older browsers.

2) Defined Fallback
-------------------

This is a fallback that takes advantage of the fact that a browser applies the
last known declaration. Just recall the grunt-pixrem post-processor from one of
the previous chapters:

```css
.element {
  /* Dinosaur browsers */
  font-size: 16px;
  /* Modern browsers */
  font-size: 1rem;
}
```

This is a good solution for all new CSS3 units, RGBa values and flexbox layouts.

You will most certainly remember that we used a defined fallback when dealing
with prefixed variants of CSS properties:

```css
.element {
  /* Chrome, Safari, Android:  */
  -webkit-column-count: 2;
  /* Firefox: */
  -moz-column-count: 2;
  /* IE 10, Op 11.1+: */
  column-count: 2;
}
```


3) Detecting CSS Properties Support
-----------------------------------

Unfortunately, it is not possible to use a natural fallback for some properties.
The solution for older browsers is either to create a different user interface
or to apply a different code structure.

Here feature detection comes into play. However, I would like to express mild
outrage over using browser detection. You may ask: “What the hell is browser
detection?” In the past, by using CSS hacks or detecting User Agent signatures
we were able to pinpoint a particular browser that does not understand certain
properties. That was OK to do when there were two or three older versions of
Internet Explorer.

Nowdays, every CSS3 property is supported (or not supported) by a different
group of browsers. Sometimes, it is just Internet Explorer prior to version 8,
sometimes Internet Explorer 9 and lower, sometimes Opera Mini - and sometimes
even older Android browsers join the club. Who knows what will come in a year’s
time. Therefore, it is much easier to detect feature support, not browser
support. We can then forget about the browsers.

Feature detection is useful when using the SVG vector format which I have
already mentioned:

```css
.icon {
  background-image: url(icon.svg);
}

.no-svg .icon {
  background-image: url(icon.png);
}
```

When it comes to CSS3 properties, it is useful for the layout-related ones.
let’s make a flexbox example:

```css
.component {
  display: flex;
}

.no-flexbox .component {
  display: table;
}
```

Or a multi-column layout:

```css
.text {
  columns: 2;
}

.no-csscolumns .text {
  float: left;
  width: 50%;
}
```

Modernizr adds “detection” classes like .no-svg. This javascript library is
mentioned in the chapter on tools. Alternatively, you can write your own
detection javascript.

### Feature Queries

Currently, Modernizr is *sort of* natively supported by W3C. This
support comes in the form of CSS Feature Queries. Thanks to the `@supports`
at-rule, you can query the availability of a particular CSS property:

```css
.component {
  display: table;
}

@supports (display: flex) {
  display: flex;
}
```

See more at [developer.mozilla.org/en-US/docs/Web/CSS/@supports](https://developer.mozilla.org/en-US/docs/Web/CSS/@supports).

### Empty Media Query

An interesting use of feature detection (and a by-the-book example of
Progressive Enhancement!) is an empty media query. Older browsers like IE8 and
other “prehistoric dinosaurs” will simply not recognize this part of the code.
This is suitable if you want to declare layout for modern browsers only:

```css
.component {
  /* Basic rules for
typography and linear design */
}

@media only screen {
  .component {
    /* Layout and other
  non-trivial rules */
  }
}
```

Let’s remember this motto:

-   In older browsers, the key thing is the availability of the main content,
    not following the graphic design to the letter.
-   Linear display is better than a broken site layout.

4) Polyfills
------------

These are Javascript libraries simulating the support of new features in
browsers that do not support them. They are very popular among Javascript
developers but will sure help HTML/CSS coders as well. Perfect examples of this
are Respond.js which turns on CSS3 Media Queries support in older Internet
Explorers and Picturefill, which makes responsive images work – `<img srcset
sizes>` and `<picture>`.

However, apart from the proven
[Respond.js](https://github.com/scottjehl/Respond) I do not recommend using
CSS3 polyfills. They usually deteriorate performance of the website and the
visual part is dependent on Javascript.

5) Generated Fallback
---------------------

We have already mentioned cssnext and post-processing but now that we are
dealing with fallbacks, we have to do it one more time.

A good alternative to Respond.js, which will provide you with a functional
website even in browsers without Media Queries support, is
[grunt-legacssy](https://github.com/robinpokorny/grunt-legacssy), which
generates a CSS version without Media Queries.

Generated fallback is just an automated way to create a defined fallback as
illustrated in the
[grunt-pixrem](https://github.com/robwierzbowski/grunt-pixrem) example.
