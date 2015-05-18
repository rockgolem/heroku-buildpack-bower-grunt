## Heroku buildpack: Grunt and Bower asset pipeline

Rockgolem's buildpack for running our asset pipeline.

This is a fork of [Heroku's official Node.js buildpack](https://github.com/heroku/heroku-buildpack-nodejs) with support for [Grunt](http://gruntjs.com/) and [Bower](http://bower.io/).

> This buildpack assumes you are using [Heroku buildpack multi](https://github.com/ddollar/heroku-buildpack-multi).

Usage
-----

* Add this buildpack to your current app:

```
heroku config:add BUILDPACK_URL=https://github.com/ddollar/heroku-buildpack-multi.git
```

* Create your Node.js app and add a Gruntfile named `gruntfile.js` with a `heroku` task:

```
grunt.registerTask('heroku', 'clean less mincss');
```

* Create a `.buildpacks` file and add the following (or add to it):

```
https://github.com/heroku/heroku-buildpack-nodejs.git
https://github.com/rockgolem/heroku-buildpack-bower-grunt.git
```


Don't forget to add grunt to your dependencies in `package.json`. If your grunt tasks depend on other pre-defined tasks make sure to add these dependencies as well:

```json
"devDependencies": {
    "grunt": "*",
    "grunt-contrib": "*",
}
```

Push to heroku

```
$ git push heroku master
...
=====> Heroku receiving push
=====> Fetching custom buildpack... done
-----> Node.js app detected
-----> Found Bower file, running bower installation.
...
-----> Found gruntfile, running grunt heroku task
Running "heroku" task
...
-----> Discovering process types
```

Further Information
-------------------

* [Heroku: Buildpacks](https://devcenter.heroku.com/articles/buildpacks)
* [Buildpacks: Heroku for Everything](http://blog.heroku.com/archives/2012/7/17/buildpacks/)
* [Grunt: a task-based command line build tool for JavaScript projects](http://gruntjs.com/)
* [Bower](http://bower.io)
