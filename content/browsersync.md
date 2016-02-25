Live Preview: BrowserSync
=========================

BrowserSync is a very useful helper when developing websites locally. It allows
you to sync file changes with a browser preview and to browse websites using
connected devices.

If you modify a CSS or HTML file, you will see the changes in a browser - you
guessed it - without a page reload. Most of us are familiar with this anyway.

You can also display a local version of your website in a mobile browser.
BrowserSync will help you with the IP address and when operating within the site
(i.e. clicking links, filling in forms, scrolling). BrowserSync will perform
identical actions on all connected devices.

BrowserSync and Grunt
---------------------

BrowserSync is fully compatible with both Grunt and Gulp so all you need to do
is install it and add the following configuration:

```javascript
browserSync: {
  dev: {
    bsFiles: {
      src : [
        'dist/css/*.css'
      ]
    },
    options: {
      watchTask: true,
      proxy: 'project.localhost'
    }
  }
}
```

When you run a task, your command line will look something like this:

```bash
$ grunt browserSync
Running “browserSync:dev” (browserSync) task
[BS] Proxying: http://project.localhost
[BS] Access URLs:
 --------------------------------------
       Local: http://localhost:3000
    External: http://192.168.0.104:3000
 --------------------------------------
          UI: http://localhost:3001
 UI External: http://192.168.0.104:3001
 --------------------------------------
[BS] Watching files...
```

This way, BrowserSync will run your project at `http://localhost:3000` as a
proxy for your local URL `project.localhost`.

Your mobile device will be able to connect to the same network at
`http://192.168.0.104:3000`.

Use the same URLs and port 3001 to display the BrowserSync app user interface.

The `watchTask: true` option in your task config says that all files are watched
by the `watch` plugin (when changing files or you perform other operations) and
BrowserSync will not stand in the way.

See more at [browsersync.io](http://www.browsersync.io/).
