Font Face – tips & tricks
=========================

Beware of faux bold and faux italics
------------------------------------

Are you using your own font files on a website? In other words: are you not
using cloud solutions such as Google Fonts? Then it is good to know that if you
want to use fonts in various sizes and variants, you have to make appropriate
CSS declarations and have files with appropriate cuts ready.

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
<p>Grumpy wizards make toxic brew for the <b>evil</b>
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Queen and Jack.

… the word „evil” will be rendered as bold at first sight, as well as the word
„Jack” will be rendered as italic thanks to the italic cut of the `WebFont`
family. But don't be fooled - this is the case of faux italics and bold cut that
the browser tried to render from a normal cut of the font.

Pokud všechny tři řezy potřebujete, jediná správná cesta je dodat prohlížeči tři
řezy – „normální“, kurzívu a tučný řez — a v CSS deklaraci mu oznámit, který
soubor ke které variantě patří.

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

Více na
[css-snippets.com/web-fonts-faux-bold-and-italic/](<http://css-snippets.com/web-fonts-faux-bold-and-italic/>).

Načítání fontů z jiných domén v Internet Exploreru
--------------------------------------------------

Díky bezpečnostnímu pravidlu o servírování fontů ze stejného původu (same origin
policy) je v IE všech verzí (ale i starých Chrome a Firefoxech) zakázáno načítat
soubory s fonty z jiné domény. Dozvíte se to, když vám Explorer do konzole
nahlásí:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
CSS3117: @font-face failed cross-origin request. Resource access is restricted.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Řešením je správně nastavit `.htaccess` na doméně, z níž servírujete soubory s
písmy:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
<IfModule mod_headers.c>
  <FilesMatch "\.(eot|otf|tt[cf]|woff2?)$">
    Header set Access-Control-Allow-Origin "*"
  </FilesMatch>
</IfModule>
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Nastavení pro jiné servery než Apache hledejte v `server-configs` repozitářích u
HTML5Boilerplate — [github.com/h5bp](<https://github.com/h5bp>).

Fontokuk
--------

Chamurappiho užitečný nástroj na testování přítomnosti (nejen) českých znaků v
souborech v písmech. Vyberete font z operačního systému, z Google Fonts nebo
přilinkujete vlastní a také vyberete text, který v něm chcete vysázet. Ten vám
pak Fontokuk vykreslí ve vybraném písmu –
[fontokuk.webylon.info](<http://fontokuk.webylon.info>).

Ikonfonty
---------

Zajímavý způsob využití webových fontů představují tzv. „ikonfonty“. Namísto
běžných znaků jsou v nich uložené ikonky.

Výhodou je vektorový formát, který vám umožní mít jednu verzi ikony pro všechny
velikosti rodičovského prvku nebo pro všechny možné varianty vysokokapacitních
displejů.

Aplikace IcoMoon vám vygeneruje fonty s ikonami na míru –
[icomoon.io](<http://icomoon.io>).

Hezké využití ikonfontů je vektorová mapa Česka –
[cezetmap.cz](<http://cezetmap.cz>).

Než se do používání ikonfontů pustíte, zvažte, zda pro vás není lepší použít
rovnou vektorový formát SVG –
[css-tricks.com/icon-fonts-vs-svg/](<http://css-tricks.com/icon-fonts-vs-svg/>).
