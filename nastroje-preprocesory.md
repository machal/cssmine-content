CSS Preprocessors
=================

LESS, SASS and other preprocessors make a front-end developer's life a little
easier. Preprocessors precede CSS. They add new properties and simplify the
code. Then they are complied into CSS so all web browsers can understand.

Preprocessor Features
---------------------

### Variables

You sure know them from imperative programming language and you would not
believe how handy they might come when writing CSS.

I can change the primary color of my Bootstrap implementation simply by changing
it on another level. The LESS notation looks like this:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
@brand-primary: #428bca;
@import "bootstrap/bootstrap";
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The rival Foundation framework can operate with variable queries. The
`$small-up` variable has an entire media query in it so you do not have to write
it again and again. The SASS notation looks like this:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
$medium-up: "only screen and (min-width: 40em)";
@media #{$medium-up} {
  // Your code for viewport width 40em an up
}
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

### Nesting

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
.nav {
  // …

  @media only screen and (min-width: 768px) {
    width: 25%;
  }
}
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

This will be compiled into:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
@media only screen and (min-width: 768px) {
  .nav {
    width: 25%;
  }
}
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

It seems useless but this is one of the reasons I started to use CSS
preprocessors. When using CSS, most browsers will not understand nested Media
Queries and you tend to organize your code using Media Queries. Component
organization is more favorable though. In the above example, the `.nav` module
will be the main organizational unit and Media Queries will be nested in it.
That is what we want.

### Mixins

Your CSS code tends to repeat itself… Therefore, mixins are the basic building
blocks of CSS, i.e. properties that can used in various other rule-sets, just by
calling a class.

A typical use of a non-parametric mixin to force element to self-clear (LESS):

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
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
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

This will be compiled into:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
.el {
  &:before,
  &:after {
    content: " "; 
    display: table;
  }
  &:after {
    clear: both;
  }
}   
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Mixins can also have parameters and that's where the fin starts!

### @import

If you import a partial component written in a preprocessor, the `@import`
at-rule will not behave as you might expect in CSS where it creates additional
requests. Moreover, these requests are a pain in the butt because they slow down
the page load, especially on mobile devices.

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
@import "module.less";
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

If you import a standard CSS file, the preprocessors will keep the @import
directive in the compiled code. You can change this behavior by setting the LESS
property:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
@import (less) "fancybox.css";
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

### Additional Features

Preprocesors have plenty of additional features. Let's take a look at them:

-   [lesscss.org/features/](<http://lesscss.org/features/>)

-   [sass-lang.com/guide](<http://sass-lang.com/guide>)

However, every complex feature makes the code a little less comprehensive. Out
of my experience, I tend to make simpler code and use the most important
features of a preprocessor. If you work in a team, simplicity of the CSS code is
of great importance.

### Which Preprocessor to Choose?

If I make it simple, I will give you two recommendations:

-   If you are a novice or a coder mainly dealing with CSS, choose LESS.

-   If you are a programmer and you are familiar with Javascript or PHP, choose
    SASS.

There is a complex text on this topic on my blog –
[vzhurudolu.cz/blog/15-css-preprocesory-4](<http://www.vzhurudolu.cz/blog/15-css-preprocesory-4>).

You do not have to take this decision too seriously though. Switching from one
preprocessor to another will not give you a headache.

The Disadcantages of CSS Preprocessors
--------------------------------------

-   It's too powerful – stepping away from a dumb CSS leads to elaborated and
    sometimes imperative code, however it tends to be incomprehensive and hard
    to maintain. You know what they say about the "good servant but a bad
    master", don't you?

-   The code is proprietary – if you use preprocessors bluntly, teaching a
    novice or swithing to another preprocessor is a piece of cake. However, it
    gets worse when you combine it with the previous point.

I think that some problems that are now solved by preprocessors will be
addressed in the postprocessing phase in the near future. So let's dig into the
Node.js chapter, shall we?
