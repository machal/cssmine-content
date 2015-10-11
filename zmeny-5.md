SVG and srcset/sizes, a New Challenge for Image Inserting
=========================================================

Thanks to the CSS pixels and the need to reduce file size, there are a lot more
problems to solve than a simple question - "Should I use PNG or JPG?".

Before we start, we have to divide web site images into two categories –
interface images and content images.

Interface Images: Icons, Logotypes, Enhancements
------------------------------------------------

The only sustainable approach is to use vector graphics. [Font
icons](<https://css-tricks.com/examples/IconFont/>) are a good but temporary
solution. The SVG vector format, on the other hand, offers much more interesting
options.

When dealing with interface enhancement (custom shadows, buttons or borders…),
the best way is to use CSS3 or alternatively SVG.

Content Images: Photos
----------------------

You can export images in huge resolutions (i.e. four times higher) and reduce
their sizes in HTML.

This way, you will solve the `device-pixel-ratio` problem, however the file size
of your web site will be so high, the users will track you down and beat you to
death with their mobile phones.

Just a reminder: an image optimized for Retina displays (2x) does not contain
twice the number of pixels (2x) but four times the number of pixels (4x). So its
file size can also be four times the size.

Therefore, I recommend to use new attributes of the `<img>` tag — `srcset` and
`sizes`.
