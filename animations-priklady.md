Examples of CSS3 Animation
==========================

First: Blinking Box
-------------------

This simple example will teach you the absolute basics of CSS animation. The
elements opacity will be changed in an infinite loop on mouse hover.

First, define the progress of the animation using `@keyframes`:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
@keyframes my_blink_animation {
    0% { opacity: 1; }
    50% { opacity: 0; }
    100% { opacity: 1; }
}
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

We have just defined a `my_blink_animation` which will set a full opacity at the
beginning of the animation (`opacity`).  In one half of the duration time
(`50%`) the element will be fully transparent (invisible) and at the end of the
animation, it will be fully opaque. In other words, the element will blink.

The animation will apply if a user hovers over the element with a mouse. Or
using alternative ways for that matter:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
.example:hover,
.example:focus,
.example:active {
    animation: my_blink_animation 1s infinite;
}
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

In this example, an animation called `my_blink_animation` will last for one
second and will iterate an infinite (`infinite`) number of times.

You can try the example at
[cdnp.io/e/pKodf](<http://codepen.io/machal/pen/pKodf>). And just for the
record: try it but avoid using it in practice! :-)

Second: Multiple Animations
---------------------------

The second example is a little more advanced. It combines two animations and
makes use of the animation direction along with other methods we have learned
before.

First, let's define both animations:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
@keyframes rotate {
    to {
        transform: rotate(45deg);
    }
}   

@keyframes pulse {
    to {
        transform: scale(1.2);  
    }       
}
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

If you have already read about [transformations](<css3-transforms.md>), you know
that a `rotate` animation will rotate an element by 45 degrees to the right and
a `pulse` animation will scale it by 20 %. Notice that you do not have to
declare the initial state (`from` or `0%`). CSS declarations that the element
already has will take effect when the animation is applied.

The animation will be applied if a user takes action: first the `move` animation
will be executed, then the `pulse` animation with a 1 second delay from the
previous one.

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
.element:hover,
.element:focus,
.element:active {
    animation: 
        rotate 250ms, 
        pulse 500ms 1s infinite;
}
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

You can try the example at
[cdpn.io/e/xipAj](<http://codepen.io/machal/pen/xipAj>).
