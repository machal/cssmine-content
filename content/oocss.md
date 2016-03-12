Sustainable Code Using OOCSS
============================

OOCSS stands for “Object Oriented CSS”. It is a code organization system by
Nicole Sullivan.

A CSS object is a repeating visual component which can be expressed as a piece
of HTML and CSS/Javascript. It is reusable in various places in your code and
across multiple projects.

The objective of OOCSS is to provide developers with reusable code, improve its
maintenance and reduce CSS file size.

Let’s take the example of a simple CSS button:

```css
/* Component */
.button { … }

/* Component elements */
.button-icon { … }

/* Component modifiers */
.button-primary { … }
.button-login { … }
```

In my understanding, OOCSS has five principles:

1) Visual Presentation Independent of Structure
-----------------------------------------------

Never put HTML tags into CSS as these tags may change. Use `.button` rather than
`input.button`.

2) Content Independent of Container
-----------------------------------

Never reflect the HTML structure in CSS as it may change. Use
`.button.button-login` rather than `.login-form .button`.

3) Component Oriented Development, Reusability
----------------------------------------------

Components (i.e. objects) that are not dependent on the HTML structure can be
easily used on other projects. They form a closed unit that we can import using
a preprocessor.

```css
@import 'button';
```

They make both our code and repository commits uncluttered.

4) Object, Element, Modifier
----------------------------

We have three types of elements:

-   object – a component or a block (`.button`)
-   element – an entity inside an object or a sub-object (`.button-icon`
    representing an icon within a button)
-   modifier – an object property (`.button-primary` representing the main
    call-to-action button)

It might come in handy to distinguish these three element types visually when
working with bigger projects.

5) The Lowest Specificity
-------------------------

In CSS, do not use identificator selectors (`#id`). The `!important` clause is
reserved for debugging purposes only.

To ensure the lowest specificity possible, avoid using:

-   child selector (do not use `.button.button-icon`, but rather
    `.button-icon`)
-   combined selectors (do not use `.button.button-primary`, but rather
    `.button-primary`)

Find more on CSS specificity at
[specificity.keegan.st](http://specificity.keegan.st/).
