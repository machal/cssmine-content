CSS3 Text Overflow – A Way To Wrap Text
=======================================

This is a way of limiting text that exceeds the width of the element and
inserting 3 dots.

```css
text-overflow: ( clip | ellipsis | <_string_> );
```

When showing `text-overflow: ellipsis` in my lectures, I always get two kinds of
reactions. One half of the audience is bored, saying: "Hm, I have been using
this for two years already…" And the other half? Enthusiastically taking notes:
"I must use this first thing tomorrow!"

However, the catch when using the `ellipsis` value is that it will apply to a
single line of text in block elements and 3 dots ("…") will be shown if the line
is overflown. Nevertheless, it is still a time saver.

Navigation Example
------------------

Imagine a navigation bar where you do not want the text to be broken onto the
next line. Plus you do not know either its length or the width of the box it is
in.

In such a case, just extend the `ellipsis` declaration by two other declarations
that will ensure that the text stays on one line:

```css
text-overflow: ellipsis;
overflow: hidden;
white-space: nowrap;
```

Try resizing the browser window at this example URL:
[cdpn.io/e/FeLkJ](<http://cdpn.io/e/FeLkJ>).

Browser Support
---------------

`text-overflow: ellipsis` is supported in all browsers, even in IE6, so there is
no problem.
