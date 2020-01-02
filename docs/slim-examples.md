# Examples

## Example config

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

## Compile

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

## Concat and compile

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

## Compile multiple files

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
