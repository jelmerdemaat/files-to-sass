# Files to Sass

Converts a list of files to (a map of) Sass variables with their content.

[GitHub](https://github.com/jelmerdemaat/files-to-sass) |
[NPM](https://www.npmjs.com/package/files-to-sass) |
[@jelmerdemaat](https://twitter.com/jelmerdemaat)

Early beta: see [todo](#todo) for functionality that's not yet included.

### Configuration

`filesToSass(options, callback(Object fileList));`

Use as follows:

```js
var filesToSass = require('files-to-sass');

filesToSass({
    src: '/path/to/source/folder/',
    dest: '/path/to/dest/file.scss',
    sassMap: true,
    sassMapName: 'MyFiles',
    base64: true
    debug: true,
}, callback);
```

Using [Gulp](http://gulpjs.com) it's possible to access this module directly:

```js
var filesToSass = require('files-to-sass');

gulp.task('import', function () {
    filesToSass({
        src: '/path/to/source/folder/',
        dest: '/path/to/dest/file.scss',
        sassMap: true,
        sassMapName: 'MyFiles',
        base64: true
        debug: true,
    }, callback);
});
```

Example output, using SVG's as input, would be:

```scss
$logo: '<svg width="58" height="56" viewBox="0 0 58 56"><g fill="#163962"...';
$icon-download: '<svg width="12" height="12" viewBox="0 0 12 12"><g fill="#000"...';
$icon-arrow-right: '<svg width="15" height="15" viewBox="0 0 15 15"><g fill="#fd0"...';
```

And using the Sass map functionality:
```scss
$fileMap: (
    logo: '<svg width="58" height="56" viewBox="0 0 58 56"><g fill="#163962"...',
    icon-download: '<svg width="12" height="12" viewBox="0 0 12 12"><g fill="#000"...',
    icon-arrow-right: '<svg width="15" height="15" viewBox="0 0 15 15"><g fill="#fd0"...'
);
```

#### Options

##### options.src
Required. Sets the path to the source folder.

##### options.dest
Required. Sets the path and name of the destination Sass file, including extension.

##### options.sassMap
Optional. Set to true if you want to output a Sass map.

Default: ```false```

##### options.sassMapName
Optional. String to be used as the Sass map variable name. The `$` will be prepended.

Default: ```fileMap```

##### options.base64
Optional. Convert strings to Base64

Default: ```false```

##### options.imageSizes
Optional. Only available when using Sass maps and (SVG) images. Returns width and height in addition to the file contents.

Default: ```false```

##### options.debug
Optional. Set to true if you want to see which files are being processed.

Default: ```false```

### Todo

* Switch to async module structure.
* Add ability to use files as source input.
* ~~Add the output folder if it doesn't exist already.~~
* ~~Add option to use maps in stead of plain variables.~~ Thanks [@sebsmi](https://github.com/sebsmi)
