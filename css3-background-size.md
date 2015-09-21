CSS3 Background Size
====================

Specifies the size of a background within an element.

Syntax
------

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
background-size:
    (cover/contain)
    _vertical_size_
    _horizontal_size_;
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The default value `background-size: auto auto` tells the browser to maintain the
original size of the image.

As with other CSS properties, we can set the width and height simultaneously –
`background-size: auto`.

### `cover` and `contain`

The key word `cover` tells the browser to cover the whole area of an element.
`contain`, on the other hand, tells the browser to show the whole image.

`background-size: cover` is typically used to make sure an image covers the
whole website background – see an example at
[alistapart.com/d/supersize-that-background-please/index3.html](<http://alistapart.com/d/supersize-that-background-please/index3.html>)

`background-size: contain` is typically used when placing an icon as a
background of an element that resizes according to various screen resolutions or
if you want to use double or triple the size of an image due to high-resolution
displays. See
[studiopress.com/design/css-background-size-graphics.htm](<http://www.studiopress.com/design/css-background-size-graphics.htm>)

Tip: If you tend to work with icons this way, consider using a vector solution
(SVG or font icons) –
[css-tricks.com/icon-fonts-vs-svg/](<http://css-tricks.com/icon-fonts-vs-svg/>).

### Size in `px` nebo percentage

The *vertical\_size* and *horizontal\_size* values can be defined in standard
CSS units – `px`, `em` and other.

When using percentage, the values are relative to the width or height of an
elment to which the property is applied. For example: stretching a gradient
background to the full width and one half of the height of an element would look
like this:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
background: linear-gradient(to bottom, transparent, black) no-repeat bottom;
background-size: 100% 50%;
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Take a look at a live example at
[codepen.io/machal/pen/cmpjE](<http://codepen.io/machal/pen/cmpjE>).

Nezapomeňte, že šířka nebo výška pozadí vychází z nastavení vlastnosti
[background-origin](<css3-background-origin.md>). Standardně se tedy
`padding-box` a `background-size` počítá z vnitřního okraje a obsahu elementu.

### Více obrázků na pozadí

Pokud používáme [více obrázků na pozadí](<css3-multiple-backgrounds.md>),
specifikace změn jejich velikostí opět oddělujeme čárkou:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
background-size: 50% auto, auto;
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Podpora v prohlížečích
----------------------

`background-size` zvládají všechny dnešní prohlížeče kromě IE8 –
[caniuse.com/background-img-opts](<http://caniuse.com/background-img-opts>).

### `background-size` v IE8

Univerzální řešení neexistuje, na míru své situace si můžete vybrat z těchto
čtyř:

Nedělat nic. Pokud obrázek dobře vyberete, nemusíte se v některých situacích
trápit tím, že se v IE8– nezmenší.

Detekce vlastností. Poskytnout alternativní verzi stylování pomocí Modernizru –
`.no-backgroundsize .element { … }`.

Využít parametru `filter`. Hodí se jen pro situace, kdy obrázek na pozadí máte
ve stejném poměru stran a zároveň stejně velký nebo větší než rodičovský objekt:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
.element {
    background-size: contain;
    filter: progid:DXImageTransform.Microsoft.AlphaImageLoader(
        src='images/image.jpg',
        sizingMethod='scale');
}
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Využít polyfill. Jen pozor, využívá `.htc` soubory, takže může nepřiměřeně
zhoršovat výkon –
[github.com/louisremi/background-size-polyfill](<https://github.com/louisremi/background-size-polyfill>).
