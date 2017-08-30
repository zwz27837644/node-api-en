<!-- YAML
added: v5.10.0
changes:
  - version: v7.0.0
    pr-url: https://github.com/nodejs/node/pull/7079
    description: Passing a negative `size` will now throw an error.
-->

* `size` {integer} The desired length of the new `Buffer`

Allocates a new `Buffer` of `size` bytes.  If the `size` is larger than
[`buffer.constants.MAX_LENGTH`] or smaller than 0, a [`RangeError`] will be
thrown. A zero-length `Buffer` will be created if `size` is 0.

The underlying memory for `Buffer` instances created in this way is *not
initialized*. The contents of the newly created `Buffer` are unknown and
*may contain sensitive data*. Use [`Buffer.alloc()`] instead to initialize
`Buffer` instances to zeroes.

Example:

```js
const buf = Buffer.allocUnsafe(10);

// Prints: (contents may vary): <Buffer a0 8b 28 3f 01 00 00 00 50 32>
console.log(buf);

buf.fill(0);

// Prints: <Buffer 00 00 00 00 00 00 00 00 00 00>
console.log(buf);
```

A `TypeError` will be thrown if `size` is not a number.

Note that the `Buffer` module pre-allocates an internal `Buffer` instance of
size [`Buffer.poolSize`] that is used as a pool for the fast allocation of new
`Buffer` instances created using [`Buffer.allocUnsafe()`] and the deprecated
`new Buffer(size)` constructor only when `size` is less than or equal to
`Buffer.poolSize >> 1` (floor of [`Buffer.poolSize`] divided by two).

Use of this pre-allocated internal memory pool is a key difference between
calling `Buffer.alloc(size, fill)` vs. `Buffer.allocUnsafe(size).fill(fill)`.
Specifically, `Buffer.alloc(size, fill)` will *never* use the internal `Buffer`
pool, while `Buffer.allocUnsafe(size).fill(fill)` *will* use the internal
`Buffer` pool if `size` is less than or equal to half [`Buffer.poolSize`]. The
difference is subtle but can be important when an application requires the
additional performance that [`Buffer.allocUnsafe()`] provides.

