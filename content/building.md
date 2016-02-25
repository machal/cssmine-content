Building Stuff: Prepros, Grunt, Gulp
====================================

It almost always comes in handy to be able to execute certain operations that
affect the source code in general. We want to compile CSS from a preprocessor,
minify it, or minify Javascript files and merge them - to name just a few
operations. We also want to reduce the size of images and merge them into a CSS
sprite.

Therefore, the direct link to source files in HTML has been replaced by
optimized distribution versions. And now we're getting there: to make these
distribution versions, we need building tools.

The building tools for the front-end come in two types:

-   simplified – they are simple to use, but their functions are limited
    (Prepros, CodeKit and other)
-   full-featured – their functions are almost unlimited but they are hard for
    beginners or non-programmers to tackle (Grunt, Gulp and other)

Prepros
-------

This is an example of a simplified building tools I usually recommend starting
with it as it is supported by all platforms and it has a point-and-click user
interface.

![Prepros](dist/images/original/prepros.jpg)

Apart from the ability to perform all basic CSS, Javascript and image tasks,
Prepos also has an FTP deployment feature and a synchronized website testing
tool for multiple devices.

Grunt
-----

It is necessary to mention that in order to use Grunt, you have to be familiar
with the command line. No other advanced knowledge is needed. To be honest, I
tiptoe around the command line, however Grunt has become my “buddy” quite
quickly.

Grunt can be installed using NPM…

```bash
NPM install -g grunt-cli
```


… and then you install one of the plugins, e.g. a plugin for compiling LESS to
CSS:

```bash
NPM install grunt-contrib-less --save-dev
```


By using plugins, namely using `Gruntfile.js`, you can create Grunt tasks. This
is a simplified example of such a file:

```javascript
module.exports = function(grunt) {
  “use strict";
  grunt.initConfig({
    pkg: grunt.file.readJSON('package.json'),

    less: {
      default: {
        files: {
          'dist/css/style.css': 'src/less/index.less'
        }
      }
    },

    cssmin: {
      css: {
        files: {
          'dist/css/style.min.css': 'dist/css/style.css'
        }
      }
    },

    watch: {
      less: {
        files: 'src/less/**/*.less',
        tasks: ['css']
      }
    }
  });

  grunt.registerTask('css', ['less', 'cssmin']);
  grunt.registerTask('default', ['watch']);
};
```


First, you need to configure `less`, `cssmin` and `watch` plugins in order to
create `css` and `default` “task aliases”. Then you can add a queue of other
tasks.

At the beginning of a project, you just run a `default` task using the `grunt`
command and then you can track file changes.

See more at [gruntjs.com](http://gruntjs.com/).

Gulp
----

Gulp can do basically the same things as Grunt but it's faster and configures
tasks using Javascript. Therefore, it is easier to generalize stuff and is more
suitable for programmers and larger projects.

See more at [gulpjs.com](http://gulpjs.com/).
