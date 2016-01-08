CSS3 Selectors
==============

CSS3 marches in with an army of new selectors. Let's look at it through the lens
of Internet Explorer. Depending on what version of IE you have to support, you
can use the following selectors:

IE8+
----

-   `span[att^="val"]` – the `attr` attribute value that starts with a "val"
    string. Is is widely used by CSS frameworks for making grids. Classes such
    as `.span1`, `.span2` etc. are targeted like this: `span[class^="span"]`

-   `span[att$="val"]` – the `attr` attribute value that ends with a "val"
    string.

-   `span[att*="val"]` – the `attr` attribute value that contains a "val"
    string.

-   `p ~ ul` – unlike `p + ul`, they both have the same parent but are
    non-adjacent.

IE9+
----

-   `span:empty` – targets all `<span>` elements that have no child elements or
    text.

-   `div:target` – targets the link anchor (`/url#anchor`).

-   `input:enabled`, `input:disabled` – targets a form field that is read only.

-   `input:checked` – targets an active input type `checkbox`, `radio` or
    `option`.

-   `*::selection` – styling of selected text.

-   `span:not(.blue)` – targets all spans except the ones with the `blue` class.

-   `:first-child`, `:last-child`, `:only-child` – targets the first, last or
    the only child of a parent.

-   `:nth-child(n)`, `:nth-last-child(n)` – targets an n-th child from the start
    or end. You can master this crazy (yet very useful) selector using this
    online tool: [NthMaster](http://nthmaster.com/).

-   `:first-of-type`, `:last-of-type`, `:only-of-type` – targets the first, last
    or one of a type element.
