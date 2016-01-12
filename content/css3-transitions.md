CSS3 Transitions – Simple Transition Animations
===============================================

This will help you animate property changes.

It may sound complicated but just imagine this situation:

```css
.box {
  background: green;
}

.box:hover {
  background: blue;
}
```

Not a big deal. Now imagine you want to animate the color change on mouse hover.
And that is what transitions are for. They animate property changes.

```css
.box {
  background: green;
  transition: 300ms;
}

.box:hover {
  background: blue;
}
```

CSS transitions are usually triggered on mouse hover but you can also trigger
them by adding a class using Javascript and clicking on the element:
`.box.clicked { background: blue; }`.

Try an example at [cdpn.io/e/hJljB](http://cdpn.io/e/hJljB).

In Practice
-----------

This way, we can animate almost any CSS property including positioning or
[transformation](css3-transforms.md).

You can actually have a lot of fun using transitions. You can animate borders or
create [wild hover
animations](http://tympanus.net/Tutorials/OriginalHoverEffects/).

However, it is not a fully-fledged animation tool. If you want to have the
progress of the animation completely under control, take a look at [CSS3
animations](css3-animations.md).

But that does not mean you can't steal the show using transitions. Just read on.

Syntax
------

```css
transition:
  (_transition_property_)
  _transition_duration_
  (_transition_timing_function_)
  (_transition_delay_)
  (, _additional_transition_);
```

### Transition Duration

This is the only required value in the `transition` shorthand, defined in
seconds or milliseconds. A separate declaration looks like this
`transition-duration: 0s`.

### Transition Properties

Not all element properties can be animated, leaving the rest without animation.
A separate declaration would look like this: `transition-property: none`.
Example:

```
.box {
  background: green;
  transition: margin 300ms;
}

.box:hover {
  background: blue;
  margin-left: 200px;
}
```

As mentioned before, animated transitions cannot be applied on all CSS
properties. For instance, animating the `display` property would be absolutely
useless. So here is [list of animatable
properties](http://www.w3.org/TR/css3-transitions/#animatable-properties).

### Transition Timing Function

A separate declaration would look like this: `transition-timing-function: ease`.
You can choose from [preset
values](http://www.w3.org/TR/css3-transitions/#transition-timing-function) or
you can define [your own](http://matthewlein.com/ceaser/).

### Transition Delay

A transition can be delayed, causing the property change to be executed a
specified time after the request. A separate declaration would look like this:
`transition-delay: 0s`.

### Multiple Animations

If you are changing multiple properties, you do not have to animate them at
once. You can easily combine them, opening up new dimension of animation
possibilities.

Both transitions in the following example last 200 milliseconds. However, the
second one which animates the `background-color` property is executed 1s after
the first one has ended:

```
transition:
  transform 200ms,
  background-color 200ms 1s;
```

Take a look at the following example at
[cdpn.io/e/vIGAk](http://cdpn.io/e/vIGAk).

Browser Support
---------------

IE10+. If you use CSS `transition` for eye candy effects (not as a function),
you can pull it off much easier than by using Javascript plus no one will miss
it in older browsers.

On the other hand, if you are creating a functional animation (e.g. a progress
bar), make an alternative fallback solution for older browsers using feature
detection.
