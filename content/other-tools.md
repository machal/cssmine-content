Other Tools and Websites
========================

Now, let's move quickly.

HTML5 Please
------------

This website will tell you under what conditions it is recommended to use each
CSS3 (or HTML5) property. In other words, it will tell you whether or not to use
a particular property and whether to use it using a prefix or a polyfill. When
using certain properties, it is better to wait until they are fully supported.
Just take these as general recommendations and always take into account the
particular target audience of your website.
[html5please.com](http://html5please.com)

Can I Use
---------

"Can I Use” is a website containing tables with information on which browsers
can and do support a specific property and which do not. If you must remember
just one website, this is the one. This website can also be interconnected with
your Google Analytics stats. However, it is quite clear that support of browser
properties on a global scale offers no guarantees when it comes to your own
project. [caniuse.com](http://caniuse.com)

Should I Prefix
---------------

Shall I use a prefixed version when using specific CSS3 properties? This website
might come in handy, but using an Autoprefixer is a much better solution. You
can find references to Autoprefixer in the previous chapters of this e-book.
[shouldiprefix.com](http://shouldiprefix.com)

Modernizr
---------

This is a javascript library for feature detection. Pick a CSS3 or HTML5 feature
you are using on a particular project and the Modernizr webiste will generate a
piece of code that you can insert into your own code. In CSS, you can then use
conditions such as `.no-flexbox .form`. In javascript you can use something like
this: `if (Modernizr.canvas) { … }`. [modernizr.com](https://modernizr.com)

Project Templates
-----------------

If you do not fancy doing projects from scratch, take a look at HTML5
Boilerplate - a default HTML template. This has proved effective as a knowledge
base but I do not recommend using it on real projects.
[html5boilerplate.com](https://html5boilerplate.com)

A more massive project base is Web Starter Kit by Google. Apart from ready-made
HTML, CSS and JS files, you can find a complete Gulp workflow there.
[developers.google.com/web/starter-kit/](https://developers.google.com/web/starter-kit/)

Moreover, a lot of templates (even quite complex ones) can be found in Yeoman
generators.[yeoman.io/generators/](http://yeoman.io/generators/)

Documentation
-------------

Superb documentation of new web technologies and CSS3 properties can be found at
the Mozilla Developer Network.
[developer.mozilla.org/en-US/docs/Web/CSS/CSS3](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS3).

And just for the record: the content of this e-book can also be found at
[cssmine.com](http://www.cssmine.com).

More Advanced Tools
-------------------

As I have already mentioned in the introduction, in general it is not wise to
overrate tools. In this e-book, I focus on beginner and intermediate front-end
developers. If you see yourself as an advanced developer, you should not miss
tools such as Broccoli, Browserify, Webpack or CSSNext. If you are into
Javascript, take a look at Babel and Traceur.

That's it. Enjoy!
