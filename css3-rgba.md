CSS3 RGBa Color – Semi-transparent Color
========================================

It is a RGB color with a forurth parameter (number) which is an alpha
transparency channel.

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
rgba(_red_, _green_, _blue_, _transparency_);
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Semi-transparent RGBa colors can be applied anywhere in CSS where a color is
comonly used. Just to mention a few: borders, [shadows](<css3-box-shadow.md>) or
[gradients](<css3-gradients.md>).

A Comparison With `opacity`
---------------------------

`opacity: 0.5` will make an element and all its children semi-transparent.

RGBa is a color that can be applied to any element without influencing the rest
of it. I.e. you can use it for background color `background: rgba(20%, 100%,
20%, .5)`.

Take a look at [cdpn.io/e/HrBsD](<http://cdpn.io/e/HrBsD>).

Browser Support 
----------------

All browsers except IE 8 and older versions have no problem with rendering RGBa.
However, using a defined fallback, you can respectfully deal with "the elderly":

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
color: rgb(128, 0, 0);
color: rgba(255, 0, 0, 0.5);
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

This fallback will be rendered by modern browsers as a red color with a 50%
transparency. IE8 will render it as a dark shade of red. A fallback color must
be defined with respect to the background color which is black in this case.

You can alternatively use
[CSS3Pie](<http://css3pie.com/documentation/supported-css3-features/>).
