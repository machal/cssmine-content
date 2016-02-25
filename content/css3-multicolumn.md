CSS3 Multi-column Layout
========================

Thanks to this module, you can put text into multiple columns of a specified
width, similar to newspaper typesetting.

The module consists of several properties:

```css
column-width: _column_width_;
column-count: _column_count_;
column-gap: _gap_between_columns_;
column-rule: _property_of_vertical_line_between_columns_;
```

Apart from this “newspaper typesetting”, the module is also applicable to list
items, image thumbnails and online store items.

Example
-------

Let's define a column width using the `column-width: 15em` declaration and
define a gap between the columns using `column-gap: 2em`.

You can see a vertical line example, `column-rule: 1px dotted #ddd`, at the link
below.

If you resize the browser window and there is not enough space for multiple
columns, the browser itself will lose the multi-column layout.

You can try it at [cdpn.io/e/ohLgJ](http://cdpn.io/e/ohLgJ).

Browser Support
---------------

IE10+. I recommend handling older browsers by using a hard fallback – in that
case, the text will simply not form columns.
