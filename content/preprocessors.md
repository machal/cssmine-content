CSS Preprocessors
=================

LESS, SASS and other preprocessors make a front-end developer's life a little
easier. Preprocessors precede CSS. They add new properties and simplify the
code. Then they are complied into CSS so all web browsers can understand it. It
is as simple as that.

Preprocessor Features
---------------------

### Variables

You sure know them from imperative programming languages and you would not
believe how handy they might come in when writing CSS.

For example, I can change the primary color of a Bootstrap implementation (using
LESS) simply by changing it on another level - using a preprocessor. The LESS
notation looks like this:

```less
@brand-primary: #428bca;
@import "bootstrap/bootstrap";
```

The rival Foundation framework (using SASS) can operate with variable queries.
Let's explain it, shall we? The Foundation framework can operate with a
`$medium-up` variable which contains an entire media query so you do not have to
write it again and again. The SASS notation looks like this:

```scss
$medium-up: "only screen and (min-width: 40em)";
@media #{$medium-up} {
  // Your code for viewport width 40em an up
}
```

### Nesting

```css
.nav {
  // …

  @media only screen and (min-width: 768px) {
    width: 25%;
  }
}
```

This will be compiled into:

```css
@media only screen and (min-width: 768px) {
  .nav {
    width: 25%;
  }
}
```

It seems useless but this is one of the reasons I started to use CSS
preprocessors. When using CSS, most browsers will not understand nested Media
Queries and as a result, you tend to organize your code using Media Queries.
Component organization is more favorable though. In the above example, the
`.nav` module will be the main organizational unit and Media Queries will be
nested in it. That's what we want.

### Mixins

Your CSS code tends to repeat itself… Therefore, mixins are the basic building
blocks of CSS, i.e. properties that can be used in various other rule-sets, just
by calling a class.

This is a typical use of a non-parametric mixin to force an element to
self-clear (LESS):

```less
.clearfix() {
  &:before,
  &:after {
    content: " ";
    display: table;
  }
  &:after {
    clear: both;
  }
}

.el {
  .clearfix;
}
```

This will be compiled into:

```css
.el:before,
.el:after {
  content: " ";
  display: table;
}
.el:after {
  clear: both;
}
```

Mixins can also have parameters and that's where the fun starts!

### @import

If you import a partial component written in a preprocessor, the `@import`
at-rule will not behave as you might expect in CSS where it creates additional
requests. Moreover, these requests are a pain in the butt because they slow down
the page load, especially on mobile devices.

```less
@import "module.less";
```

If you import a standard CSS file, the preprocessors will keep the @import
directive in the compiled code. You can change this behavior by setting the LESS
property:

```less
@import (less) "fancybox.css";
```

### Additional Features

Preprocessors have plenty of additional features. Let's take a look at them:

-   [lesscss.org/features/](http://lesscss.org/features/)
-   [sass-lang.com/guide](http://sass-lang.com/guide)

However, every complex feature makes the code a little less comprehensive. Out
of my experience, I tend to make simpler code and use the most important
features of a preprocessor. If you work in a team, simplicity of the CSS code is
of great importance.

### Which Preprocessor to Choose?

If I make it simple, I will give you two recommendations:

-   If you are a novice or a coder mainly dealing with CSS, choose LESS.
-   If you are a programmer and you are familiar with Javascript or PHP, choose
    SASS.

You do not have to take this decision too seriously though. Switching from one
preprocessor to another will not give you a headache.

The Disadvantages of CSS Preprocessors
--------------------------------------

-   They are too powerful – stepping away from a dumb CSS leads to elaborated
    and sometimes imperative code, however it tends to be in-comprehensive and
    hard to maintain. You know what they say about the “good servant but a bad
    master”, don't you?
-   The code is proprietary – if you use preprocessors bluntly, teaching a
    novice or switching to another preprocessor is a piece of cake. However, it
    gets worse if you combine it with the previous point.

I think that some problems that are now solved by preprocessors will be
addressed in the post processing phase in the near future. So let's dig into the
Node.js chapter, shall we?
