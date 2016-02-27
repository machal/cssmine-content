CSS3 Animations – Full-featured Animations
==========================================

You might be surprised but these are the first native web animations ever. Is
that really surprising? All existing animation methods are either encapsulated
in their own technological framework (Gif, Flash, Silverlight, etc.) or they
animate using a method that was not designed for that purpose: Javascript.

So what is the difference between an animation and a transition? When using
(`animation`), you basically can control the particular event much better.
Moreover, you are not limited to the CSS properties that the animated object has
before the animation starts. Transitions (`transition`), on the other hand, are
meant for simple animated transitions which go from one state to another.

Syntax
------

First, you have to define an animation using the `@keyframes` at-rule. Then you
can call it anywhere and adjust it to your needs.

```css
@keyframes _animation_name_ {
  _duration_ { _property_declaration_ }
  _duration_ { _property_declaration_ }
}

#example {
  animation:
    _animation_name_
    _animation_duration_
    _animation_timing_function
    _animation_delay_
    _animation_iteration_count_
    _animation_direction_
    _animation_fill_mode_
    (,_additional_animations_);
}
```

Now, let’s explain all properties:

### `animation-name`

This can be used separately as `animation-name: my_animation`.

### `animation-duration`

Set it in seconds (`.5s`) or milliseconds (`500ms`). The default value is
`animation-duration: 0s`.

### `animation-timing-function`

This is similar to [transition](css3-transitions.md). You can use the
pre-defined function or define your own. A separate declaration with a default
value looks like this: `animation-timing-function: ease`.

### `animation-delay`

This is the specified time the animation will wait before it is executed. The
value is defined in seconds and milliseconds and the default value is null:
`animation-delay: 0`.

### `animation-iteration-count`

The interaction can be set as a number or as an “infinite number” using the
`infinite` key word. The default value is `animation-iteration-count: 1`.

### `animation-direction`

Unlike transitions, the animation keyframe will default back to its original
state (0%) when iterated and then continue to its target. If we want to blend
several animations smoothly, we need to set the animation-direction property to
the `alternate` value. It is used separately as `animation-direction:
alternate`.

### `animation-fill-mode`

The default state of our animation will look like this: before the animation
starts and after the animation has ended, no CSS properties from the animation
keyframes are applied to the animated element. However, using the
`animation-fill-mode` property, we can change that.

Four properties can be applied:

-   `none` - the default value.
-   `backwards` - this value will apply values defined in the keyframe 0% even
    if the element has different property settings.
-   `forwards` - after the iteration of an animation ends, the object will
    remain in the same state as in keyframe 100% and will not go back.
-   `both` - this will apply both `forwards` and `backwards`.

### `animation-play-state`

This property is not a part of the animation shorthand and is to be used
separately. You can temporarily stop the animation by using the
`animation-play-state: paused` declaration. I imagine the function of the
`running` value is self-explanatory.

### `@keyframes` – Frames of the Animation Sequence

Keyframes define the animation start (using the `from` key word or `0%`),
progress (using percentage of the duration) and end (using the `to` key word or
`100%`). The change between keyframes is defined by the browser and you only
have to set the start and end. The number of keyframes is not limited.

Browser Support
---------------

CSS3 animations are not supported by IE prior to version 9:
[caniuse.com/#feat=css-animation](http://caniuse.com/#feat=css-animation)

The strategy for supporting animations in older browsers depends heavily on the
type of animation.

When using animations as an **enhancement** (i.e. for aesthetical purposes in
the user interface which the user will not miss if not executed), there is no
reason to search for an alternative solution.

If, however, the animation **carries information** (e.g. a progress bar when
loading a file), it is necessary to substitute a CSS3 animation for Javascript
or detect browsers which do not support CSS3 animations and come up with an
alternative solution for them.
