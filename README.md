# grunt-slim-html

> Compile Slim to HTML



## Getting Started
This plugin requires Grunt `^1.0.4`

If you haven't used [Grunt](http://gruntjs.com/) before, be sure to check out the [Getting Started](http://gruntjs.com/getting-started) guide, as it explains how to create a [Gruntfile](http://gruntjs.com/sample-gruntfile) as well as install and use Grunt plugins. Once you're familiar with that process, you may install this plugin with this command:

```shell
npm install grunt-slim-html --save-dev
```

Once the plugin has been installed, it may be enabled inside your Gruntfile with this line of JavaScript:

```js
grunt.loadNpmTasks('grunt-slim-html');
```




## Slim task
_Run this task with the `grunt slimhtml` command._

This task requires you to have [Ruby](http://www.ruby-lang.org/en/downloads/) and [Slim](http://slim-lang.com/). If you're on OS X or Linux you probably already have Ruby installed, try `ruby -v` in your terminal. When you've confirmed you have Ruby installed, run `gem install slim` to install Slim.

### Options

#### trace
Type: `Boolean`

Show a full traceback on error.

#### bundleExec
Type: `Boolean`

Run `slimrb` preceding it with `bundle exec`.

#### compile
Type: `Boolean`

Compile only but do not run.

#### rails
Type: `Boolean`

Generate rails compatible code (Implies --compile).

#### translator
Type: `Boolean`

Enable translator plugin.

#### logicLess
Type: `Boolean`

Enable logic less plugin.

#### pretty
Type: `Boolean`

Produce pretty html.

#### option
Type: `String|Array`

Set slim option.

### Examples

#### Example config

```javascript
grunt.initConfig({
  slimhtml: {                              // Task
    dist: {                            // Target
      files: {                         // Dictionary of files
        'index.html': 'index.slim',     // 'destination': 'source'
        'sidebar.html': 'sidebar.slim'
      }
    },
    dev: {                             // Another target
      options: {                       // Target options
        pretty: true
      },
      files: {
        'index.html': 'index.slim',
        'page.html': [
          'header.html',
          'body.html',
          'footer.html'  // Maybe you need one extra file in dev
        ]
      }
    }
  }
});

grunt.loadNpmTasks('grunt-slim-html');

grunt.registerTask('default', ['jshint', 'slimhtml']);
```

#### Compile

```javascript
grunt.initConfig({
  slimhtml: {
    dist: {
      files: {
        'index.html': 'index.slim'
      }
    }
  }
});
```

#### Concat and compile

If you specify an array of `src` paths they will be concatenated. However, in most cases you would want to just `render` them into `index.slim`.

```javascript
grunt.initConfig({
  slimhtml: {
    dist: {
      files: {
      'index.html': [
          'header.html',
          'content.html'
        ]
      }
    }
  }
});
```

#### Compile multiple files

You can specify multiple `destination: source` items in `files`.

```javascript
grunt.initConfig({
  slimhtml: {
    dist: {
      files: {
        'index.css': 'index.slim',
        'sidebar.html': 'sidebar.slim'
      }
    }
  }
});
```

#### Globbing Files

You can specify an entire directory of files that should get compiled into individual files with the specified extension.
Example: if `path/to` contained `a.slim` and `b.slim`, the following target would generate these files in `path/to/dest`: `a.html` and `b.html`.

```javascript
grunt.initConfig({
  slimhtml: {
    dist: {
      files: [{
        expand: true,
        cwd: 'path/to',
        src: ['{,*/}*.slim'],
        dest: 'path/to/dest',
        ext: '.html'
      }]
    }
  }
}
```

## Release History

 * 2020-01--2   v0.0.1   Initial release.
