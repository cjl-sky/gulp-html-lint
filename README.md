# gulp-html-lint

## Usage

```js
var gulp = require('gulp'),
  htmlLint = require('gulp-html-lint');

gulp.task('html', function() {
  return gulp
    .src('site/**/*.html')
    .pipe(htmlLint())
    .pipe(htmlLint.format())
    .pipe(htmlLint.failOnError());
});
```

## API

### Functions

- **htmlLint([opts])** - Adds `htmlLint` property to every file in a stream that is incorrect. Handles [options](#options).
- **htmlLint.failOnError()** - Fail when an HtmlLint error is found in HtmlLint results.
- **htmlLint.failAfterError()** - Fail when the stream ends and if any HtmlLint error(s) occurred. `failOnError` failed immediately - did not wait for the stream to end.
- **htmlLint.format([formatter])** - Formats all HtmlLint issues using given formatter or a default one.
- **htmlLint.formatEach([formatter])** - Format the results of each file individually.
- **htmlLint.result(action)** - Handle each HtmlLint result as it passes through the stream.
- **htmlLint.results(action)** - Handle all HtmlLint results at the end of the stream.

### Options

- **htmllintrc** - (String, default: `".htmllintrc"`) [htmllintrc](https://github.com/htmllint/htmllint/wiki/Options) configuration file.
- **useHtmllintrc** - (Boolean, default: `true`) if `false` does not load htmllintrc configuration file.
- **rules** - (Object, default: `{}`) Additional htmllint rules.
- **plugins** - ([String], default: `[]`) List of htmllint plugins.
- **limitFiles** - (Number, default: `Number.MAX_VALUE`) Stops linter after defined number of invalid files.
- **limitIssuesPerFile** - (Number, default: `Number.MAX_VALUE`) Stops linter after defined number of linter issues in one file.
- **limitIssues** - (Number, default: `Number.MAX_VALUE`) Stops linter after defined number of linter issues.

Default **opts** values:

```js
{
    htmllintrc: ".htmllintrc",
    useHtmllintrc: true,
    rules: {},
    plugins: [],
    limitFiles: `Number.MAX_VALUE`,
    limitIssuesPerFile: `Number.MAX_VALUE`,
    limitIssues: `Number.MAX_VALUE`,
}
```

## Build process

### Gulp commands

- `gulp lint` - runs code checkstyle
- `gulp test` - runs tests
- `gulp test --file test/loader.js` - runs single test file `./test/loader.js`
- `gulp` - alias for `gulp lint test`
- `gulp test-cov` - runs instrumented tests, generates reports to `./build/test`
- `gulp test-cov --file test/loader.js` - runs single instrumented test file `./test/loader.js`
- `gulp clean` - removes `./build` folder
- `gulp ci` - alias for `gulp clean lint test-cov`

### NPM commands

- `npm test` - alias for `gulp test`
- `npm run ci` - alias for `gulp ci`

## License

[MIT](LICENSE) © cjl-sky
