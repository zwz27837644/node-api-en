<!-- YAML
added: v0.1.16
changes:
  - version: v6.0.0
    pr-url: https://github.com/nodejs/node/pull/5348
    description: Passing a non-string as the `path` argument will throw now.
-->

* `path` {string}
* Returns: {string}

The `path.dirname()` method returns the directory name of a `path`, similar to
the Unix `dirname` command. Trailing directory separators are ignored, see
[`path.sep`][].

For example:

```js
path.dirname('/foo/bar/baz/asdf/quux');
// Returns: '/foo/bar/baz/asdf'
```

A [`TypeError`][] is thrown if `path` is not a string.

