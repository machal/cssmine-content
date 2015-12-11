CSS3 Font Face – BYOF (bring your own font...)
==============================================

Web fonts a.k.a. "your own fonts in a website"? The `@font-face` property is
nowdays a standard technique with almost full compatibility with all browsers so
there is no need to fear it from the technological point of view.

Syntax
------

First declare the font family and path to a file using the `@font-face` at-rule:

```css
@font-face {
    font-family: _font_family_name_;
    src: url(_path_to_a_font_file_)
      format(_file_format_);
}
```

Then simply call the font family in standard CSS:

```css
.element {
        font-family: _font_family_name_;
}
```

File Formats of Web Fonts
-------------------------

If you are not using a cloud solution such as Typekit or Google Fonts and you
are using your own font files, you need to have at least a minimum knowledge of
file formats:

-   **WOFF** (Web Open Font Format) – it is the predominant file format.
    However, it is supported by MSIE from version 9 and by Android Browser from
    version 4.4 – [caniuse.com/woff](http://caniuse.com/woff)
-   **TTF/OTF** (TrueType/OpenType) – these are two formats which are supported
    by almost all modern browsers, however MSIE supports them from version 9.
    Furthermore, you have to set the so called "embedding bits" (embedding
    permissions in the font's header) to "installable".
    [caniuse.com/ttf](http://caniuse.com/ttf)
-   **SVG** (SVG vector format defined fonts) – you will need it if you want to
    support really old versions of iOS Safari browser — 4.3 and lower.
    [caniuse.com/svg-fonts](http://caniuse.com/svg-fonts)
-   **EOT** (Embedded OpenType font) – it is supported by all Internet Explorers
    from version 4. You will need it if you want to support IE8 and lower.
    [caniuse.com/eot](http://caniuse.com/eot)

### Syntax That Will Maximize Compatibility

If you need to support all browsers, the code is a little more complicated:

```css
@font-face {
    font-family: 'MyWebFont';
    /* IE9 in compatibility mode: */
    src: url('webfont.eot');
    src:
      /* IE6-IE8: */
      url('webfont.eot?#iefix')
        format('embedded-opentype'),
      /* All modern browsers: */
      url('webfont.woff')
        format('woff'),
      /* Older Safari, Android, iOS: */
      url('webfont.ttf')
        format('truetype'),
      /* iOS 4.3 and lower */
      url('webfont.svg')
        format('svg');
}
```

These days, we will most likely need just the WOFF and TTF formats (due to older
Androids) and EOT (due to IE8−). But there is a bright future ahead of us. It is
call WOFF.

### WOFF Is Our Future

In a few years, or months for that matter, the WOFF format will be the only
thing we will need:

```css
@font-face {
    font-family: 'WebFont';
    src: url('webfont.woff');
}
```

But be careful. There will always be browsers (or situations) that are not
compatible with any of these web font formats. Opera Mini is a good example. Or
imagine a situation where a modern browser does not load the web font – let's
say due to a slow mobile internet connection.

Remember that these scenarios might happen and do not forget to define a
fallback system font. Here is an example:

```css
.element {
    font-family: 'WebFont', Georgia, sans-serif;
}
```
