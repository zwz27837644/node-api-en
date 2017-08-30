<!-- YAML
added: v0.1.21
changes:
  - version: v8.1.0
    pr-url: https://github.com/nodejs/node/pull/13173
    description: Added times as numbers.
-->

Objects returned from [`fs.stat()`][], [`fs.lstat()`][] and [`fs.fstat()`][] and
their synchronous counterparts are of this type.

 - `stats.isFile()`
 - `stats.isDirectory()`
 - `stats.isBlockDevice()`
 - `stats.isCharacterDevice()`
 - `stats.isSymbolicLink()` (only valid with [`fs.lstat()`][])
 - `stats.isFIFO()`
 - `stats.isSocket()`

For a regular file [`util.inspect(stats)`][] would return a string very
similar to this:

```console
Stats {
  dev: 2114,
  ino: 48064969,
  mode: 33188,
  nlink: 1,
  uid: 85,
  gid: 100,
  rdev: 0,
  size: 527,
  blksize: 4096,
  blocks: 8,
  atimeMs: 1318289051000.1,
  mtimeMs: 1318289051000.1,
  ctimeMs: 1318289051000.1,
  birthtimeMs: 1318289051000.1,
  atime: Mon, 10 Oct 2011 23:24:11 GMT,
  mtime: Mon, 10 Oct 2011 23:24:11 GMT,
  ctime: Mon, 10 Oct 2011 23:24:11 GMT,
  birthtime: Mon, 10 Oct 2011 23:24:11 GMT }
```

*Note*: `atimeMs`, `mtimeMs`, `ctimeMs`, `birthtimeMs` are [numbers][MDN-Number]
that hold the corresponding times in milliseconds. Their precision is platform
specific. `atime`, `mtime`, `ctime`, and `birthtime` are [`Date`][MDN-Date]
object alternate representations of the various times. The `Date` and number
values are not connected. Assigning a new number value, or mutating the `Date`
value, will not be reflected in the corresponding alternate representation.


