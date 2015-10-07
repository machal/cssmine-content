Building stuff: Prepros, Grunt, Gulp
====================================

It almost always come in handy to be able to execute certain operations that
affect the source code in general. We want to compile CSS from a preprocessor,
minify it, minify Javascript files and merge them - to name just a few
operations. We also want to reduce size of images and merge them into a [CSS
sprite](<http://jecas.cz/css-sprite>).

Therefore, a direct link to the source fiels in the HTML was replaced by
optimized distribution versions. And now we're getting there: to make these
distribution versions, we need building tools.

The building tools for front-end come in two types:

-   simplified – they are simple to use, yet their functions are limited
    (Prepros, CodeKit and other)

-   full-featured – their functions are almost unlimited but they are hard to
    tackle for beginners or non-programmers (Grunt, Gulp and other)

Prepros
-------

This is a representative of simplified building tools. I usually recommend to
start with it as it is supported by all platforms and it has a point-and-click
user interfaces.

![Prepros](<images/prepros.jpg>)

Apart from all basic CSS, Javascript and image tasks, it also has an FTP
deployment feature and synchronized website testing on multiple devices.

Grunt
-----

It is necessary to mention that to use Grunt, you have to be familiar with the
command line. No other advanced knowledge is needed. To be honest, I tiptoe
around the command line, however me and Grunt have become buddies quite fast.

Grunt can be installed using npm…

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
npm install -g grunt-cli
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

… and then you install one of the plugins, e.g. a plugin for compiling LESS to
CSS:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
npm install grunt-contrib-less --save-dev
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Using plugins, namely using `Gruntfile.js`, you can create Grunt tasks. This is
a simplified example of the file:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
module.exports = function(grunt) {
  "use strict";
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
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

First, you need to confiugure `less`, `cssmin` and `watch` plugins in order to
create `css` and `default` „task aliases“. Then you can add a queue of other
tasks.

At the beginning of a project, you just run a `default` task using the `grunt`
command and you can track file changes.

See more at [gruntjs.com](<http://gruntjs.com/>).

Gulp
----

Gulp can do basically the same as Grunt but it's faster and configures tasks
using Javascript. Therefore, it is easier to generalize stuff and is more
suitable for programmers or larger projects.

See more at [gulpjs.com](<http://gulpjs.com/>).
