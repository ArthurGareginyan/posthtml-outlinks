# PostHTML OutLinks <img align="right" width="220" height="200" title="PostHTML logo" src="http://posthtml.github.io/posthtml/logo.svg">

`posthtml-outlinks` is a [PostHTML](https://github.com/posthtml/posthtml) plugin to add `target="_blank"` and attribute `rel` with the `nofollow`, `noopener`, `noreferrer` value to all external links.

**Before:**

```html
<a href="http://example.com/">External Link</a>
<a href="/">Internal Link</a>
```

**After:**

```html
<a href="http://example.com/" target="_blank" rel="nofollow noopener noreferrer">External Link</a>
<a href="/">Internal Link</a>
```
