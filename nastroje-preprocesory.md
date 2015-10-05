CSS Preprocessors
=================

LESS, SASS and other preprocessors make a front-end developer's life a little
easier. Preprocessors precede CSS. They add new properties and simplify the
code. Then they are complied into CSS so all web browsers can understand.

Preprocessor Features
---------------------

### Variables

You sure know them from imperative programming language and you would not
believe how handy they might come when writing CSS.

I can change the primary color of my Bootstrap implementation simply by changing
it on another level. The LESS notation looks like this:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
@brand-primary: #428bca;
@import "bootstrap/bootstrap";
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The rival Foundation framework can operate with variable queries. The
`$small-up` variable has an entire media query in it so you do not have to write
it again and again. The SASS notation looks like this:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
$medium-up: "only screen and (min-width: 40em)";
@media #{$medium-up} {
  // Your code for viewport width 40em an up
}
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

### Nesting

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
.nav {
  // …

  @media only screen and (min-width: 768px) {
    width: 25%;
  }
}
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

This will be compiled into:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
@media only screen and (min-width: 768px) {
  .nav {
    width: 25%;
  }
}
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

It seems useless but this is one of the reasons I started to use CSS
preprocessors. When using CSS, most browsers will not understand nested Media
Queries and you tend to organize your code using Media Queries. Component
organization is more favorable though. In the above example, the `.nav` module
will be the main organizational unit and Media Queries will be nested in it.
That is what we want.

### Mixins

Your CSS code tends to repeat itself… Therefore, mixins are the basic building
blocks of CSS, i.e. properties that can used in various other rule-sets, just by
calling a class.

A typical use of a non-parametric mixin to force element to self-clear (LESS):

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
.clearfix() {
  &:before,
  &:after {
    content: " "; 
    display: table;
  }
  &:after {
    clear: both;
  }
}

.el {
  .clearfix;
}
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

This will be compiled into:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
.el {
  &:before,
  &:after {
    content: " "; 
    display: table;
  }
  &:after {
    clear: both;
  }
}   
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Mixins can also have parameters and that's where the fin starts!

### @import

Pokud importujete parciální komponentu napsanou v preprocesoru, nechová se
`@import` tak, jak jste zvyklí z CSS, kde vytváří requesty navíc. A requesty
bolí, protože zpomalují načítání stránky, hlavně na mobilních zařízeních.

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
@import "module.less";
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Pokud importujeme běžný CSS soubor, preprocesory ve zkompilovaném kódu zachovají
direktivu @import. Toto chování můžeme změnit nastavením vlastnosti LESS:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
@import (less) "fancybox.css";
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

### Další vlastnosti

Preprocesory mají mnoho a mnoho dalších vlastností. Podívejte se na ně:

-   [lesscss.org/features/](<http://lesscss.org/features/>)

-   [sass-lang.com/guide](<http://sass-lang.com/guide>)

Každá složitější vlastnost ale komplikuje srozumitelnost CSS kódu. Autorovi se
osvědčilo trvat na jednodušším kódu a z preprocesorů si brát jen ty
nejdůležitější vlastnosti. Pokud pracujete v týmu, je jednoduchost CSS obzvlášť
důležitá.

### Jaký preprocesor zvolit?

Když to hodně zjednoduším, mám dvě rady:

-   Pokud s preprocesory začínáte nebo jste kodér a píšete hlavně CSS, zvolte
    LESS.

-   Pokud jste programátor a píšete i JavaScript nebo třeba PHP, zvolte SASS.

Složitější text o výběru jsem dříve sepisoval na blog –
[vzhurudolu.cz/blog/15-css-preprocesory-4](<http://www.vzhurudolu.cz/blog/15-css-preprocesory-4>).

Není ovšem potřeba výběr příliš prožívat. Přechod od jednoho preprocesoru k
druhému většinou moc bolestivý není.

Nevýhody CSS preprocesorů
-------------------------

-   Až moc silný nástroj – odklon od tuposti CSS a příliš mnoho abstrakce sice
    vede k propracovanému, někdy až imperativnímu kódu, zároveň ale často špatně
    čitelnému a spravovatelnému. Znáte to přísloví o dobrém sluhovi, ale špatném
    pánu, že ano?

-   Proprietární kód – pokud preprocesory využíváte „tupě“, jsou zaučení nového
    člověka nebo přechod na jiný preprocesor relativně jednoduché; horší je to
    ovšem v kombinaci v prvním bodem.

Myslím, že minimálně některé z úkolů, jež nyní řeší preprocesory, časem přejdou
do následného zpracování kódu. V dalším textu si proto nenechte ujít kapitolu o
postprocesingu.
