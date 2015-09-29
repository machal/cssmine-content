CSS3 Animations – full-featured animation
=========================================

You might be suprised but these are the first native web animations ever. Is it
surprising? All existing animation methods are either encapsulated in their own
technological framework (Gif, Flash, Silverlight ...) or they animate using a
method that was not designed for such a purpose - by javascript.

So what is the difference between an animatin and a transition? You can
basically control the particular event much better when using (`animation`).
Moreover, you are not limited by CSS properties that the animated object has
before the animation has started. Transitions (`transition`), on the other hand,
are meant for simple animated transitions from one state to another.

Syntax
------

First, you have to define an animation using the `@keyframes` at-rule. Then you
can call it anywhere and adjust it to your needs.

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
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
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

### `animation-name`

Can be used separately as `animation-name: my_animation`.

### `animation-duration`

Set it in seconds (`.5s`) or miliseconds (`500ms`). The default value is
`animation-duration: 0s`.

### `animation-timing-function`

It is similar to [transition](<css3-transitions.md>). You can use the
pre-defined function or define your own. A separate declaration with a default
value looks like this: `animation-timing-function: ease`.

### `animation-delay`

It is a specified time the animation will wait before it is executed. The value
is defined in seconds and milliseconds and the default value is null:
`animation-delay: 0`.

### `animation-iteration-count`

The interation can be set as a number or an infinite number using the `infinite`
key word. The default value is `animation-iteration-count: 1`.

### `animation-direction`

Unlike using transitions, the animation keyframe will default back to its
origial state (0%) when iterated and then continue to its target. If we want to
blend several animations smoothly, we need to set the animation-direction
property to the `alternate` value. It is separately used as
`animation-direction: alternate`.

### `animation-fill-mode`

The default state of our animation will look like this: Both before the
animation start and after the animation has ended, no CSS properties from the
animation keyframes are applied to the animated element. However, using the
`animation-fill-mode` property, we can change that.

For properties can be applied:

-   `none` — the default value.

-   `backwards` — this value will apply the values defined in the keyframe 0%
    even if the element has different property settings.

-   `forwards` — after an iteration of an animation ends, an object will remain
    in the same state as in keyframe 100% and will not go back.

-   `both` — will apply both `forwards` and `backwards`.

### `animation-play-state`

This property is not a part of the animation shorthand and is to be used
separately. You can temporarily stop the animation by using the
`animation-play-state: paused` declaration. I suppose the function of the
`running` value is self-explanatory.

### `@keyframes` – Frames of the Animation Sequence

Keyframes define the animation start (using `from` key word or `0%`), progress
(using percentage of the duration) and end (using `to` key word or `100%`). The
change between keyframes is defined by the browser and you only have to set the
start and en. The number of keyframes is not limited.

Browser Support
---------------

CSS3 animations are not supported by IE prior to version 9:
[caniuse.com/\#feat=css-animation](<http://caniuse.com/#feat=css-animation>)

The strategy of supporting animations in older browsers gravely depends on the
type of animation.

When using animations as **enhancement** (i.e. for aesthetical purposes in the
user interface which the user will not miss when not executed), there is no
reason for searching for an alternative solution.

If, however, the animation **carries an information** (i.e. a progress bar when
loading a file), it is necessary to substitute a CSS3 animation for javascript
or detect browsers which do not support CSS3 animations and come up with an
alternative solution for them.
