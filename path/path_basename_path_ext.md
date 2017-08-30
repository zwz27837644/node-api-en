<!-- YAML
added: v0.1.25
changes:
  - version: v6.0.0
    pr-url: https://github.com/nodejs/node/pull/5348
    description: Passing a non-string as the `path` argument will throw now.
-->

* `path` {string}
* `ext` {string} An optional file extension
* Returns: {string}

The `path.basename()` methods returns the last portion of a `path`, similar to
the Unix `basename` command. Trailing directory separators are ignored, see
[`path.sep`][].

For example:

```js
path.basename('/foo/bar/baz/asdf/quux.html');
// Returns: 'quux.html'

path.basename('/foo/bar/baz/asdf/quux.html', '.html');
// Returns: 'quux'
```

A [`TypeError`][] is thrown if `path` is not a string or if `ext` is given
and is not a string.

