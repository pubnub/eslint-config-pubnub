# eslint-config-pubnub
pubnub centric eslint rule-set


## installation

add the config to the package.json
```
npm install --save-dev eslint-config-pubnub
```

add  the eslint package to package.json
```
npm install --save-dev eslint
```

create a `.eslintrc.yml` for ES5:
```yaml
extends: pubnub/es5
```

or `.eslintrc.yml` for ES6:
```yaml
extends: pubnub
```

## using with [gulp](https://github.com/adametry/gulp-eslint)

install the dependency: `npm install --save-dev gulp-eslint`

and add the following configuration

```javascript
const gulp = require('gulp');
const eslint = require('gulp-eslint');

gulp.task('lint', () => {
    // ESLint ignores files with "node_modules" paths.
    // So, it's best to have gulp ignore the directory as well.
    // Also, Be sure to return the stream from the task;
    // Otherwise, the task may end before the stream has finished.
    return gulp.src(['**/*.js','!node_modules/**']) // <<< TODO TODO TODO modify me
        // eslint() attaches the lint output to the "eslint" property
        // of the file object so it can be used by other modules.
        .pipe(eslint())
        // eslint.format() outputs the lint results to the console.
        // Alternatively use eslint.formatEach() (see Docs).
        .pipe(eslint.format())
        // To have the process exit with an error code (1) on
        // lint error, return the stream and pipe to failAfterError last.
        .pipe(eslint.failAfterError());
});

gulp.task('default', ['lint'], function () {
    // This will only run if the lint task is successful...
});

```

## using with [grunt](https://github.com/sindresorhus/grunt-eslint)

install the dependency: `npm install --save-dev grunt-eslint load-grunt-tasks`

```javascript
require('load-grunt-tasks')(grunt); // npm install --save-dev load-grunt-tasks

grunt.initConfig({
    eslint: {
        target: ['file.js']
    }
});

grunt.registerTask('default', ['eslint']);
```




