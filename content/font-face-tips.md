Font Face: Tips & Tricks
========================

Beware of Faux Bold and Faux Italics
------------------------------------

Are you using your own font files on a website? In other words, are you **not**
using cloud solutions such as Google Fonts? Then it is good to know that if you
want to use fonts of various sizes and variants, you have to make appropriate
CSS declarations and have files with appropriate font cuts ready.

This applies primarily to the italic and bold cuts. If you declare the font like
this…

```css
@font-face {
  font-family: 'WebFont';
  src: url('webfont.woff');
}

.element {
  font-family: 'WebFont', Georgia, sans-serif;
}
```


… and then you apply it in HTML like this…

```css
<p>Grumpy wizards make toxic brew for
the <b>evil</b> Queen and <i>Jack</i>.</p>
```

… then the word “evil” will be rendered as bold when it first appears and the
word “Jack” will be rendered in italics thanks to the italic cut of the
`WebFont` family. But don’t be fooled - this is the case of faux italic and bold
cuts that the browser tries to render from a normal cut of the font.

If you need all three font cuts, i.e. normal, bold and italic, the only way to
achieve this is to declare all three of them and set a CSS declaration to tell
the browser which file is connected to a particular font variant.

Take a look at a simplified example:

```css
@font-face {
  font-family: 'WebFont';
  src: url('webfont.woff');
  font-style: normal;
  font-weight: normal;
}

@font-face {
  font-family: 'WebFont';
  src: url('webfont-bold.woff');
  font-style: normal;
  font-weight: bold;
}

@font-face {
  font-family: 'WebFont';
  src: url('webfont-italic.woff');
  font-style: italic;
  font-weight: normal;
}
```


See more at
[css-snippets.com/web-fonts-faux-bold-and-italic/](http://css-snippets.com/web-fonts-faux-bold-and-italic/).

Cross-origin Web Font in Internet Explorer
------------------------------------------

Thanks to the “same origin policy”, it is not permitted to load font files from
different domains. This applies to all Internet Explorer versions and some older
versions of Chrome and Firefox as well. You can see an example of this problem
in the console of your browser:

```
CSS3117: @font-face failed cross-origin request.
Resource access is restricted.
```


The solution is to set your `.htaccess` to the domain where your font files are
located:

```
<IfModule mod_headers.c>
  <FilesMatch "\.(eot|otf|tt[cf]|woff2?)$">
    Header set Access-Control-Allow-Origin "*"
  </FilesMatch>
</IfModule>
```

If you do not use an Apache server, you will have to take a look in the
`server-configs` repositories. See [github.com/h5bp](https://github.com/h5bp).

Worth mentioning is that loading from other domains slightly slows down the
display because of the extra DNS lookup.

Font Icons
----------

Font icons are a convenient way to use web fonts. They contain icons instead of
regular characters.

The indisputable advantage of using font icons is the vector format, which
allows you to use one icon for all sizes of the parent element and for all
high-resolution displays.

The IcoMoon app will generate fonts with custom icons: see
[icomoon.io](http://icomoon.io).

However, before looking into font icons, consider using the SVG vector format:
see
[css-tricks.com/icon-fonts-vs-svg/](http://css-tricks.com/icon-fonts-vs-svg/).
