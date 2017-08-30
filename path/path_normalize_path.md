<!-- YAML
added: v0.1.23
-->

* `path` {string}
* Returns: {string}

The `path.normalize()` method normalizes the given `path`, resolving `'..'` and
`'.'` segments.

When multiple, sequential path segment separation characters are found (e.g.
`/` on POSIX and either `\` or `/` on Windows), they are replaced by a single
instance of the platform specific path segment separator (`/` on POSIX and
`\` on Windows). Trailing separators are preserved.

If the `path` is a zero-length string, `'.'` is returned, representing the
current working directory.

For example on POSIX:

```js
path.normalize('/foo/bar//baz/asdf/quux/..');
// Returns: '/foo/bar/baz/asdf'
```

On Windows:

```js
path.normalize('C:\\temp\\\\foo\\bar\\..\\');
// Returns: 'C:\\temp\\foo\\'
```

Since Windows recognizes multiple path separators, both separators will be
replaced by instances of the Windows preferred separator (`\`):

```js
path.win32.normalize('C:////temp\\\\/\\/\\/foo/bar');
// Returns: 'C:\\temp\\foo\\bar'
```

A [`TypeError`][] is thrown if `path` is not a string.

