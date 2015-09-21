Font Face – tips & tricks
=========================

Beware of faux bold and faux italics
------------------------------------

Are you using your own font files on a website? In other words: are you not
using cloud solutions such as Google Fonts? Then it is good to know that if you
want to use fonts in various sizes and variants, you have to make appropriate
CSS declarations and have files with appropriate font cuts ready.

This applies primarily to the italic and bold cut. If you declare the font like
this…

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
@font-face {
    font-family: 'WebFont';
    src: url('webfont.woff');
}

.element {
    font-family: 'WebFont', Georgia, sans-serif;
}
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

… and then you apply it in HTML like this…

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
<p>Grumpy wizards make toxic brew for the <b>evil</b> Queen and Jack.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

… the word „evil” will be rendered as bold at first sight, as well as the word
„Jack” will be rendered as italic thanks to the italic cut of the `WebFont`
family. But don't be fooled - this is the case of faux italics and bold cuts
that the browser tried to render from a normal cut of the font.

If you need all three font cuts, i.e. normal, bold and italic, the only way to
achieve this is to declare all three of them — and set a CSS declaration to tell
the browser which file is connected to particular font variant.

Zjednodušeně by to mohlo vypadat takto:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
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
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Find more at
[css-snippets.com/web-fonts-faux-bold-and-italic/](<http://css-snippets.com/web-fonts-faux-bold-and-italic/>).

Cross-origin web font in Internet Explorer
------------------------------------------

Thanks to the "same origin policy", it is not permitted to load font files from
another domain. This applies to all Internet Explorer versions and some older
versions of Chrome and Firefox as well. You can see this problem in the console
of your browser:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
CSS3117: @font-face failed cross-origin request. Resource access is restricted.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The solution to this si to set your `.htaccess` on a domain where your font
files are located:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
<IfModule mod_headers.c>
  <FilesMatch "\.(eot|otf|tt[cf]|woff2?)$">
    Header set Access-Control-Allow-Origin "*"
  </FilesMatch>
</IfModule>
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

If you do not use an Apache server, you will have to take a look in
`server-configs` repositories — see
[github.com/h5bp](<https://github.com/h5bp>).

Fontokuk
--------

This is Chamurappi's very useful tool for testing the presence of special
characters in font files. Just choose either a system font, a Google Font or
insert your own code and then enter the line of text you want to see. Fontokuk
will then display the text using the desired font. See
[fontokuk.webylon.info](<http://fontokuk.webylon.info>).

Font icons
----------

Font icons are a convenient way of using web fonts. They contain icons instead
of regular characters.

The indisputable advantage of using font icons is the vector format which allows
you to use one icon for all sizes of a parent element and all high-resolution
displays.

The IcoMoon app will generate fonts with custom icons –
[icomoon.io](<http://icomoon.io>).

A nice example of using font incons is a vector map of the Czech Republic –
[cezetmap.cz](<http://cezetmap.cz>).

However, before looking into font icons, consider using the SVG vector format –
[css-tricks.com/icon-fonts-vs-svg/](<http://css-tricks.com/icon-fonts-vs-svg/>).
