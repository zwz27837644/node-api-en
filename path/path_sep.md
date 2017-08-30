<!-- YAML
added: v0.7.9
-->

* {string}

Provides the platform-specific path segment separator:

* `\` on Windows
* `/` on POSIX

For example on POSIX:

```js
'foo/bar/baz'.split(path.sep);
// Returns: ['foo', 'bar', 'baz']
```

On Windows:

```js
'foo\\bar\\baz'.split(path.sep);
// Returns: ['foo', 'bar', 'baz']
```

*Note*: On Windows, both the forward slash (`/`) and backward slash (`\`) are
accepted as path segment separators; however, the `path` methods only add
backward slashes (`\`).

