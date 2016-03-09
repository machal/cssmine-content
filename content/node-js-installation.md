Installing Node.js Ecosystem For Front-end Use
==============================================

We need Node.js on the front-end mainly for making the developers’ work easier
and for managing developer dependencies.

Tools We Will Install
---------------------

-   [Node.js](<https://nodejs.org/>) – a javascript runner from the command
    line.

-   [NPM](<https://www.npmjs.com/>) – a javascript package manager.

-   [Bower](<http://bower.io/>) - a front-end package manager (e.g. jQuery or
    Bootstrap framework).

-   [Grunt](<http://gruntjs.com/>) - an assembler or builder; a task runner for
    developers.

-   [Grunt plugins](<http://gruntjs.com/plugins>) – Grunt task plugins (e.g. for
    compiling preprocessors into CSS or files minification).

In time, you may take a fancy to [Yeoman](<http://yeoman.io/>) automators or
other tools such as [Gulp](<http://gulpjs.com/>) and
[WebPack](<https://webpack.github.io/>). They are also based on Node.js,
however, to make things simple, we will not deal with them just now.

![Node.js](<dist/images/original/node-js.svg>)

Now we will focus on the command line so it is good to know some basics. Here
are guides for installing it on [Windows](<http://dosprompt.info/basics.asp>)
and on [Linux &
Mac](<http://mac.appstorm.net/how-to/utilities-how-to/how-to-use-terminal-the-basics/>).

Node.js and NPM
---------------

NPM is a packaging system of Node.js. You have to download and install a
complete version of Node.js.

### Are You a Windows Guy? First Things First Then

1.  It is good to [install Visual Studio
    Code](<https://www.visualstudio.com/products/code-vs>). This is a code
    editor which also installs Node.js support for Windows.

2.  [Then install Git](<http://git-scm.com/downloads>) using the command line.
    In the “Adjusting your PATH environment” step, choose “Run Git from the
    Windows Command Prompt”.

And now for everyone, regardless of the platform they use. Install Node.js
globally. All the ways to do it are described here:
[nodejs.org/en/download/](<https://nodejs.org/en/download/>)

Test if everything’s OK by using the command for displaying the NPM version:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ bash
npm -v
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

All other dependencies will be installed as Node packages.

Sometimes, it is recommended to run all NPM commands as an admin (`sudo npm …`).
However, this is not good [from a security point of
view](<https://gist.github.com/leommoore/4420860#important-security-note>). It
is much better to grant the current user privileges to write into `usr/local`:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ bash
sudo chown -R $USER /usr/local
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

That is the end of this “lecture about security”. Now, let’s install useful
packages.

Grunt, Bower and Other Packages
-------------------------------

Will you use a [Grunt assembler](<grunt.md>)? Then, using the command line, you
will have to install a global package: `grunt-cli`:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ bash
npm install -g grunt-cli
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

And what about the front-end [Bower packager](<bower.md>)? That’s easy. Just
install it globally like this:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ bash
npm install -g bower
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Using the very same procedure, you can install Grunt plugins, an alternative
Gulp assembler and the Webpack.

Grunt Plugins
-------------

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ bash
npm install <plugin-name> --save-dev
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Notice that we do not install plugins globally, therefore we do not use the `-g`
switch. And yes, Grunt plugins and Bower packages can be installed in any
particular project. We really want to save them to the config files of the
package manager (`packages.json`).

Are you using Windows? Then watch out! Some Grunt plugins require special
attention. I know of
[PhantomJS](<http://attester.ariatemplates.com/usage/phantom.html>), which is a
dependency of the critical CSS
([grunt-criticals](<https://github.com/filamentgroup/grunt-criticalcss>)) plugin
or [ImageMagick](<http://www.imagemagick.org/script/binary-releases.php>) which
is indispensable for plugins that deal with images, such as
[grunt-contrib-imagemin](<https://github.com/gruntjs/grunt-contrib-imagemin>).

Bower Packages
--------------

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ bash
bower install <plugin-name> --save
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The `--save-dev` switch will save a plugin into developer dependencies.
Beginners use it in connection with Grunt and its plugins. They can be installed
using NPM.

If you want to install jQuery, it will be a user dependency. We will use the
`--save` switch but for such dependencies, it is better to use Bower.

Cheatsheet for Packaging Systems
--------------------------------

Fortunately, both Bower and NPM fortunately have similar commands:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ bash
# Searching a package in the central repository:
npm/bower search jquery-ui

# Displaying package details:
npm view jquery-ui
bower info jquery-ui

# Installing all packages on a project:
npm/bower install
# Installing a package and adding it to user dependencies:
npm/bower install jquery-ui --save
# Installing a package and adding it to developer dependencies:
npm/bower install jquery-ui --save-dev
# Installing a version specific package:
npm/bower install jquery-ui@1.11.x

# Updating all packages:
npm/bower update

# Listing a tree of dependencies:
npm/bower list
# Listing a tree of dependencies and a package version:
npm/bower list jquery-ui

# Removing a package:
npm/bower uninstall jquery-ui

# Deleting cache. Ideal when re-installing a package set:
npm cache clean

# Displaying packages that need to be updated:
npm outdated
bower list

# Help:
npm help
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
