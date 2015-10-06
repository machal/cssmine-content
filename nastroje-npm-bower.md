Package Managers: npm and Bower
===============================

Two package managers? This might be a pretty pickle for novices. In the
following paragraphs, you will find out when to use nom and when Bower.

When dealing with UI, you can use these two managers for installing two types of
packages:

-   web components – e.g. Bootstrap or jQuery and it's plugins (usually through
    Bower)

-   software for the developer's use – e.g Grunt plugins improving our workflow
    (usually through npm)

What Is a Packaging System for, anyway?
---------------------------------------

Coders haven't used any packaging system so let's explain why it is good.

First, **installation is easier** – just type `bower install jquery` and an
up-to-date version of jQuery will be installed into the `bower_components`
directory.

Second, **updates are easier** – when a new version of jQuery is released, all I
need to do is type `bower update jquery` and I have it in my project.

Also, all this **improves project manageability** – both npm and Bower
components are stored in special directories which are not versioned. Project
dependencies are versioned in npm or Bower configuration files. Thanks to that,
our repository and its history is simpler.

Node Package Manager, npm.js
----------------------------

It is a packaging system for Javascript. In the PHP world, they have Composer,
in the Javascript world, we have npm.

In my workflow, I use it mainly for installing libraries such as Grunt and it's
plugins. However, there are several approaches to packaging so it is good to
know that web libraries such as jQuery can be installed using npm too.

Npm uses a `package.json` config file and installs everything into a
`node_modules` directory.

See more at [npmjs.org](<http://npmjs.org>).

Bower
-----

Bower is a package manager system for the front-end. Components that I handle
thanks to Bower, are well beyond Javascript and they sometimes contain even CSS
and images.

In my case, Bower manages project dependencies - not just the usual jQuery
packages but also polyfills like Respond.js or Picturefill and other libraries
such as Bootstrap.

Bower uses a `bower.json` config file and installs everything into a
`bower_components` directory.

See more at [bower.io](<http://bower.io>).

A Few Useful Commands
---------------------

Fortunately, Bower adopted the npm syntax so working with it is similar.

Library search:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
npm|bower search jquery
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Installing jQuery:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
npm|bower install jquery
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Using `--save-dev` will save the library into the project's dependencies in a
`bower.json` or `package.json` config files. On the other hand, jQuery is a user
dependency so it is better to use `--save` when developing a website.

Let's move on: updating jQuery:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
npm|bower update jquery
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Installing and updating can be done within the same project at once. Both Bower
and npm compare the configuration file with the latest version of dependencies:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
npm|bower install|update
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bower vs npm
------------

Now, let's review differences in purpose:

-   npm is a package system for Javascript. A coder uses it for personal
    development needs.

-   Bower is a package system for front-end. It is used for web components.

The package systems differ not only in purpose but in saving dependencies as
well:

-   npm installs packages and their dependencies, one at a time. As a result of
    this, the directory the packages are installed into, contains multiple
    package versions. This makes perfect sense when using Grunt plugins: every
    packages requires a different dependency.

-   Bower, on the other hand, installs all dependencies at once. This also makes
    perfect sense - you want a single jQuery on a web site.

Therefore, when running a standard project, the `bower_components` directory
will contain much less data than the `node_modules` directory.
