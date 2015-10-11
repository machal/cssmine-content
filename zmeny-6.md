Vendor-Prefixed Pain in the Butt
================================

Browser developers have been implementing properties that have incomplete
standardization procedures, in other words: beta versions. To distinguish them
from the final release, they have introduced *vendor prefixes*. Fortunately,
using vendor prefixes is not as necessary as it used to be one or two years ago.

For example, if you want to declare a CSS transformation so all browsers will
understand it, you have to declare it multiple times:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
.box {
  -webkit-transform: rotate(7.5deg);  /* Chrome, Safari 3.1+ */
     -moz-transform: rotate(7.5deg);  /* Firefox 3.5-15 */
      -ms-transform: rotate(7.5deg);  /* IE 9 */
       -o-transform: rotate(7.5deg);  /* Opera 10.50-12.00 */
          transform: rotate(7.5deg);  /* Firefox 16+, IE 10+, Opera 12.10+, Chrome 36+ */
}
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

If we choose to leave out browsers that have minimal usage, we can drop `-moz`,
`-o` and sometimes even `-ms` prefixes. However, it is reasonable to generate
these vendor prefixes automatically, using a tool meant just for that.

To avoid declaring all properties manually, in the past we used CSS preprocessor
libraries such as LESShat or Compass.

Autoprefixer
------------

This problem has nowdays a rather elegant solution - an Autoprefixer:
[github.com/postcss/autoprefixer](<http://github.com/postcss/autoprefixer>).

You will simply write the CSS code as if all browsers could operate with
standardized syntax – `transform: rotate(7.5deg)`. And because Autoprefixer
happens to be a plugin for popular automation tools such as Grunt or Gulp, it
will add all vendor prefixes to your code do automatically.
