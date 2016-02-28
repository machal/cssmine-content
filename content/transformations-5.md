SVG and srcset/sizes, a New Challenge for Image Insertion
=========================================================

Thanks to CSS pixels and the need to reduce file size, there are a lot more
problems to solve than simply, “should I use PNG or JPG?”

Before we start, we have to divide website images into two categories: interface
images and content images.

Interface Images: Icons, Logotypes, Enhancements
------------------------------------------------

The only sustainable approach here is to use vector graphics. [Font
icons](https://css-tricks.com/examples/IconFont/) are a good but temporary
solution. The SVG vector format, on the other hand, offers much more interesting
options.

When dealing with interface enhancement (custom shadows, buttons or borders) the
best choice is to use CSS3 or alternatively, SVG. [css-tricks.com/using-svg/](https://css-tricks.com/using-svg/)

Content Images: Photos
----------------------

You can export images in huge resolutions (e.g. four times higher than the
original) and reduce their sizes in HTML.

You can solve the `device-pixel-ratio` problem that way.

However, the file size of your website will be so large that users will track
you down and beat you to death with their mobile phones.

Just a reminder: an image optimized for Retina displays (2x) does not contain
twice the number of pixels but four times the number of pixels (4x). So its file
size will also be four times larger.

Therefore, I recommend using the new attributes of the `<img>` tag — `srcset`
and `sizes`. [ericportis.com/posts/2014/srcset-sizes/](https://ericportis.com/posts/2014/srcset-sizes/)
