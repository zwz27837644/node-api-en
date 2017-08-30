<!-- YAML
added: v0.0.2
changes:
  - version: v7.4.0
    pr-url: https://github.com/nodejs/node/pull/10382
    description: The `buffer` parameter can now be a `Uint8Array`.
  - version: v6.0.0
    pr-url: https://github.com/nodejs/node/pull/4518
    description: The `length` parameter can now be `0`.
-->

* `fd` {integer}
* `buffer` {Buffer|Uint8Array}
* `offset` {integer}
* `length` {integer}
* `position` {integer}
* `callback` {Function}

Read data from the file specified by `fd`.

`buffer` is the buffer that the data will be written to.

`offset` is the offset in the buffer to start writing at.

`length` is an integer specifying the number of bytes to read.

`position` is an argument specifying where to begin reading from in the file.
If `position` is `null`, data will be read from the current file position,
and the file position will be updated.
If `position` is an integer, the file position will remain unchanged.

The callback is given the three arguments, `(err, bytesRead, buffer)`.

If this method is invoked as its [`util.promisify()`][]ed version, it returns
a Promise for an object with `bytesRead` and `buffer` properties.

