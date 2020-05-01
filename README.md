# PostHTML OutLinks <img align="right" width="220" height="200" title="PostHTML logo" src="http://posthtml.github.io/posthtml/logo.svg">

`posthtml-outlinks` is a [PostHTML](https://github.com/posthtml/posthtml) plugin to automatically add `target="_blank"` and the `rel` attribute with the `nofollow`, `noopener`, `noreferrer` value to all external links (configurable).

Before:

```html
<a href="http://example.com/">External Link</a>
<a href="/">Internal Link</a>
```

After:

```html
<a href="http://example.com/" target="_blank" rel="nofollow noopener noreferrer">External Link</a>
<a href="/">Internal Link</a>
```


## Install

**Method #1**

```bash
npm i posthtml posthtml-outlinks
```

**Method #2** (for Gulp)

```bash
npm i gulp-posthtml posthtml-outlinks --save-dev
```

## Usage

**Method #1**

```js
const fs = require('fs');
const posthtml = require('posthtml');
const posthtmlOutlinks = require('posthtml-outlinks');

let options = {
    excludeHosts: [
        'example.com',
        'www.example.com'
    ],
    noTarget: [],
    noRel: []
};

posthtml()
    .use(posthtmlOutlinks(options))
    .process(html)
    .then(result => fs.writeFileSync('./after.html', result.html));
```

**Method #2** (for Gulp / New method )

```js
const
    { src, dest }    = require('gulp'),
    posthtml         = require('gulp-posthtml'),
    posthtmlOutlinks = require('posthtml-outlinks');

function posthtml() {
    let plugins = [
        posthtmlOutlinks({
            excludeHosts: [
                'example.com',
                'www.example.com'
            ],
            noTarget: [],
            noRel: []
        })
    ];
    return src(`./build/*.html`)
        .pipe(posthtml(plugins))
        .pipe(dest(`./build/`));
}
```

**Method #3** (for Gulp / Old method)

```js
const gulp = require('gulp');
const posthtml = require('gulp-posthtml');
const posthtmlOutlinks = require('posthtml-outlinks');

const config = () => ({
    plugins: [
        posthtmlOutlinks({
            excludeHosts : [
                'example.com',
                'www.example.com'
            ],
            noTarget : [],
            noRel : []
        })
    ]
});

gulp.task('posthtml', () => gulp.src('./build/\*.html')
    .pipe(posthtml(config))
    .pipe(gulp.dest('./build')));

```


## Options

| Name           | Type      | Default | Property | Description      |
|:--------------:|:---------:|:-------:|:--------:|:-----------------|
| `excludeHosts` | `{Array}` | `[]`    | Required | Domains to exclude from processing |
| `noTarget`     | `{Array}` | `[]`    | Optional | Domains to which do not add `target="_blank"` |
| `noRel`        | `{Array}` | `[]`    | Optional | Domains to which do not add `rel="..."` |

> **Note!** The domain name of your current website must be specified using the `excludeHosts` option.


## Contributing

Welcome and thanks! I appreciate you taking the initiative to contribute to this project.

Contributing isn’t limited to just code. I encourage you to contribute in the way that best fits your abilities, by writing tutorials, making translation to your native language, giving a demo at your local meetup, helping other users with their support questions, or revising  the documentation for this project.

Please take a moment to read the guidelines in the [CONTRIBUTING.md](CONTRIBUTING.md) and [PostHTML Guidelines](https://github.com/posthtml/posthtml/tree/master/docs). Following them helps to communicate that you respect the time of the other contributors to the project. In turn, they’ll do their best to reciprocate that respect when working with you, across timezones and around the world.


## Security Vulnerabilities

If you discover a security vulnerability within this plugin, please send an email to me. All security vulnerabilities will be promptly addressed.


## License

This plugin is open-sourced software licensed under the [MIT](LICENSE.md) and is distributed free of charge.

Commercial licensing (e.g. for projects that can’t use an open-source license) is available upon request.


## Author

Arthur Gareginyan

* Email: arthurgareginyan@gmail.com

* GitHub: [https://github.com/ArthurGareginyan/](https://github.com/ArthurGareginyan/)

* Website: [https://www.arthurgareginyan.com](http://www.arthurgareginyan.com)

* Donation: [https://www.arthurgareginyan.com/donate.html](http://www.arthurgareginyan.com/donate.html)
