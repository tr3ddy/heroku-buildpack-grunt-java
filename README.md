heroku-buildpack-grunt-java
===========================

This is a [Heroku buildpack](http://devcenter.heroku.com/articles/buildpacks) for Java apps with Grunt for building the included frontend part(s).

The buildpack will detect your app as "Grunt+Java" if it has a `package.json` as well as a `pom.xml` file in the root.  It will use npm to install your dependencies, building the frontend with Grunt and continue building a Java app.

This is a merged fork of [Heroku's official Node.js buildpack](https://github.com/heroku/heroku-buildpack-nodejs) and [Heroku's official Java buildpack](https://github.com/heroku/heroku-buildpack-java) with added [Grunt](http://gruntjs.com/) support.
Using this buildpack you do not need to commit the results of your Grunt tasks (e.g. minification and concatination of files), keeping your repository clean.


Node.js and npm versions
------------------------

You can specify the versions of Node.js and npm your application requires using `package.json`

```json
{
  "name": "myapp",
  "version": "0.0.1",
  "engines": {
    "node": "~0.10.13",
    "npm": "~1.3.2"
  }
}
```

To list the available versions of Node.js and npm, see these manifests:

- [heroku-buildpack-nodejs.s3.amazonaws.com/manifest.nodejs](http://heroku-buildpack-nodejs.s3.amazonaws.com/manifest.nodejs)
- [heroku-buildpack-nodejs.s3.amazonaws.com/manifest.npm](http://heroku-buildpack-nodejs.s3.amazonaws.com/manifest.npm)


Usage
-----

To configure an existing app to use your buildpack:

```sh
# Create a new Heroku app that uses your buildpack
heroku create --buildpack <your-github-url>

# Configure an existing Heroku app to use your buildpack
heroku config:set BUILDPACK_URL=<your-github-url>

# You can also use a git branch!
heroku config:set BUILDPACK_URL=<your-github-url>#your-branch
```