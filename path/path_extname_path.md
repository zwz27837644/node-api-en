<!-- YAML
added: v0.1.25
changes:
  - version: v6.0.0
    pr-url: https://github.com/nodejs/node/pull/5348
    description: Passing a non-string as the `path` argument will throw now.
-->

* `path` {string}
* Returns: {string}

The `path.extname()` method returns the extension of the `path`, from the last
occurrence of the `.` (period) character to end of string in the last portion of
the `path`.  If there is no `.` in the last portion of the `path`, or if the
first character of the basename of `path` (see `path.basename()`) is `.`, then
an empty string is returned.

For example:

```js
path.extname('index.html');
// Returns: '.html'

path.extname('index.coffee.md');
// Returns: '.md'

path.extname('index.');
// Returns: '.'

path.extname('index');
// Returns: ''

path.extname('.index');
// Returns: ''
```

A [`TypeError`][] is thrown if `path` is not a string.

