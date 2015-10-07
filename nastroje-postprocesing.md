Post-processing: Autoprefixer, Pixrem and Other
===============================================

Post processing or a or subsequent processing of the CSS code is an interesting
trend in the world of CSS.

It usually stands for adding code to fallbacks for older browsers but it could
partialy replace preprocessors in a few year's time. Let's demonstrate the usage
on some post processing tools.

Autoprefixer: Adding Prefixed Declarations
------------------------------------------

Write the code according to W3C syntax …

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
transform: scale(1.1);
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

… and the Autoprefixer will then add prefixed variants into your CSS:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
-webkit-transform: scale(1.1);
-ms-transform: scale(1.1);
transform: scale(1.1);
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

By default, it will add prefixes for the two latest versions of all browsers but
you can easily change that. You just need to configure the grunt-autoprefixer, a
Grunt plugin which sets broader support of prefixed variants of CSS properties:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
autoprefixer: {
  options: {
    browsers: [
      'last 3 versions', 'ios 6',
      'ie 7', 'ie 8', 'ie 9'
    ]
  },
  style: {
      src: 'dist/css/style.css',
      dest: 'dist/css/style.css'
  }
}
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

See more at
[github.com/postcss/autoprefixer](<https://github.com/postcss/autoprefixer>).

pixrem
------

If you decide to use the `rem` unit (which I strongly recommend), you will be
faced with a compatibility problem in older browsers.

By using a pixrem plugin, you can define conversion between `rem` and `px`, thus
adding fallbacks to your CSS code:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
.box {
  margin-bottom: 24px;
  margin-bottom: 1.5rem;
}
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

See more at
[github.com/robwierzbowski/grunt-pixrem](<https://github.com/robwierzbowski/grunt-pixrem>).

legaccsy
--------

This is a plugin by Robin Pokorny that is able to create a version of your CSS
without Media Queries that are not recognized by older browsers. This is a true
life saver for IE8 or IE9.

See ore at
[github.com/robinpokorny/grunt-legacssy](<https://github.com/robinpokorny/grunt-legacssy>).

postcss
-------

As I have already mentioned, in time, postcss can replace LESS, SASS and other
preprocessors in some aspects. The philosophy is simple – CSS code is written
according to the W3C syntax, however browsers are not familiar with it. Thanks
to postcss, you can compile the code into contemporary CSS.

You might be surprised but after years of inactivity, the CSS standard is
evolving even on the syntax level.

As a result of this, CSS variables and media use the following piece of code...

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
:root {
  --fontSize: 1.2rem;
}

@custom-media --viewport-medium (width <= 600px);

@media only screen and (--viewport-medium) {
  body { font-size: calc(var(--fontSize) * 1.2); }
}
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

… which is then compiled into a well-known form:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
@media only screen and (max-width: 600px) {
  body { font-size: 1.44rem; }
}
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Postcss has a wonderful slogan:

>   Use tomorrow’s CSS syntax, today.

See more at [cssnext.io](<http://cssnext.io/>).
