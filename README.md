# @avzuykov/gulp-css-base64

## Install

Install this plugin with the command:

```js
npm install --save-dev @avzuykov/gulp-css-base64
```

## Usage

```js
var cssBase64 = require('@avzuykov/gulp-css-base64');

//Without options
gulp.task('default', function () {
    return gulp.src('src/css/input.css')
        .pipe(cssBase64())
        .pipe(gulp.dest('dist'));
});

//With options
gulp.task('default', function () {
    return gulp.src('src/css/input.css')
        .pipe(cssBase64({
            baseDir: "../../images",
            maxWeightResource: 100,
            extensionsAllowed: ['.gif', '.jpg']
        }))
        .pipe(gulp.dest('dist'));
});
```

## Options

#### options.baseDir
Type: `String`

Default value: ``

Note: If you have absolute image paths in your stylesheet, the path specified in this option will be used as the base directory. By default plugin used the current directory of gulpfile.js to find local resources.

#### options.maxWeightResource
Type: `Number`

Default value: `infinity`

#### options.extensionsAllowed
Type: `Array`

Default value: `[]`

## Ignore a specific resource

You can ignore a resource with a comment `/*base64:skip*/` in CSS file after url definition.
```css
.ignored{
  background: url(image.png); /*base64:skip*/
}

.ignored{
  background: url(image.png);
  /*base64:skip*/
}

.encoded{
  background: url(image.jpg);
}
```

## License
Copyright (c) 2022 [Mehdy Dara](https://github.com/zckrs) under the MIT License.
