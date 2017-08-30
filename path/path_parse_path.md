<!-- YAML
added: v0.11.15
-->

* `path` {string}
* Returns: {Object}

The `path.parse()` method returns an object whose properties represent
significant elements of the `path`. Trailing directory separators are ignored,
see [`path.sep`][].

The returned object will have the following properties:

* `dir` {string}
* `root` {string}
* `base` {string}
* `name` {string}
* `ext` {string}

For example on POSIX:

```js
path.parse('/home/user/dir/file.txt');
// Returns:
// { root: '/',
//   dir: '/home/user/dir',
//   base: 'file.txt',
//   ext: '.txt',
//   name: 'file' }
```

```text
┌─────────────────────┬────────────┐
│          dir        │    base    │
├──────┬              ├──────┬─────┤
│ root │              │ name │ ext │
"  /    home/user/dir / file  .txt "
└──────┴──────────────┴──────┴─────┘
(all spaces in the "" line should be ignored -- they are purely for formatting)
```

On Windows:

```js
path.parse('C:\\path\\dir\\file.txt');
// Returns:
// { root: 'C:\\',
//   dir: 'C:\\path\\dir',
//   base: 'file.txt',
//   ext: '.txt',
//   name: 'file' }
```

```text
┌─────────────────────┬────────────┐
│          dir        │    base    │
├──────┬              ├──────┬─────┤
│ root │              │ name │ ext │
" C:\      path\dir   \ file  .txt "
└──────┴──────────────┴──────┴─────┘
(all spaces in the "" line should be ignored -- they are purely for formatting)
```

A [`TypeError`][] is thrown if `path` is not a string.

