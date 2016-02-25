Package Managers: NPM and Bower
===============================

Two package managers? This might get novices into a pretty pickle. In the
following paragraphs, you will find out when to use NPM and when to use Bower.

When dealing with UI, you can use these two managers to install two types of
packages:

-   web components – e.g. Bootstrap or jQuery and its plugins (usually using
    Bower)
-   software for developers' use – e.g. Grunt plugins improving your workflow
    (usually using NPM)

What Is a Packaging System for, Anyway?
---------------------------------------

Coders are not used to using a packaging system so let's explain why it is good
to do so.

First, **installation is easier** – just type `bower install jquery` and an
up-to-date version of jQuery will be installed into the `bower_components`
directory.

Second, **updates are easier** – when a new version of jQuery is released, all
you need to do is type `bower update jquery` and you have it in your project.

Third, all this **improves project manageability** – both NPM and Bower
components are stored in special directories which are not versioned. Project
dependencies are versioned in NPM or Bower configuration files. Thanks to that,
our repository and its history are simplified.

Node Package Manager - NPM.js
-----------------------------

This is a packaging system for Javascript. In the PHP world, they have Composer,
in the Javascript world, we have NPM.

In my workflow, I use NPM mainly for installing libraries such as Grunt and its
plugins. However, there are several approaches to packaging, so it is good to
know that web libraries such as jQuery can be installed using NPM too.

Npm uses a `package.json` config file and installs everything into a
`node_modules` directory.

See more at [npmjs.org](http://npmjs.org).

Bower
-----

Bower is a package manager system for the front-end. Components that I handle
using Bower are well beyond Javascript and they sometimes even contain even CSS
and images.

In my case, Bower manages project dependencies - not just the usual jQuery
packages but also polyfills like Respond.js or Picturefill and other libraries
such as Bootstrap.

Bower uses a `bower.json` config file and installs everything into a
`bower_components` directory.

See more at [bower.io](http://bower.io).

A Few Useful Commands
---------------------

Fortunately, Bower has adopted the NPM syntax so working with it is similar to
using NPM.

Library search:

```bash
npm|bower search jquery
```

Installing jQuery:

```bash
npm|bower install jquery
```

Using `--save-dev` will save the library into the project's dependencies in a
`bower.json` or `package.json` config file. However, jQuery is a user dependency
so it is better to use `--save` when developing a website.

Let's move on: updating jQuery:

```bash
npm|bower update jquery
```


Installing and updating can be done within the same project at once. Both Bower
and NPM compare the configuration file with the latest version of dependencies:

```bash
npm|bower install|update
```


Bower vs NPM
------------

Now, let's review differences based on their purpose:

-   NPM is a package system for Javascript. A coder uses it for personal
    development needs.
-   Bower is a package system for front-end. It is used for web components.

The package systems differ not only in purpose but in the way they save
dependencies as well:

-   NPM installs packages and their dependencies one at a time. As a result of
    this, the directory into which the packages are installed contains multiple
    package versions. This makes perfect sense when using Grunt plugins - every
    packages requires a different dependency.
-   Bower, on the other hand, installs all dependencies at once. This also makes
    perfect sense - you want a single jQuery version on your website.

Therefore, when running a standard project, the `bower_components` directory
will contain much less data than the `node_modules` directory.
