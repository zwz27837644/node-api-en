<!-- YAML
added: v1.5.0
changes:
  - version: v8.0.0
    pr-url: https://github.com/nodejs/node/pull/10236
    description: The `value` can now be a `Uint8Array`.
  - version: v5.7.0, v4.4.0
    pr-url: https://github.com/nodejs/node/pull/4803
    description: When `encoding` is being passed, the `byteOffset` parameter
                 is no longer required.
-->

* `value` {string|Buffer|Uint8Array|integer} What to search for
* `byteOffset` {integer} Where to begin searching in `buf`. **Default:** `0`
* `encoding` {string} If `value` is a string, this is its encoding.
  **Default:** `'utf8'`
* Returns: {integer} The index of the first occurrence of `value` in `buf` or `-1`
  if `buf` does not contain `value`

If `value` is:

  * a string, `value` is interpreted according to the character encoding in
    `encoding`.
  * a `Buffer` or [`Uint8Array`], `value` will be used in its entirety.
    To compare a partial `Buffer`, use [`buf.slice()`].
  * a number, `value` will be interpreted as an unsigned 8-bit integer
  value between `0` and `255`.

Examples:

```js
const buf = Buffer.from('this is a buffer');

// Prints: 0
console.log(buf.indexOf('this'));

// Prints: 2
console.log(buf.indexOf('is'));

// Prints: 8
console.log(buf.indexOf(Buffer.from('a buffer')));

// Prints: 8
// (97 is the decimal ASCII value for 'a')
console.log(buf.indexOf(97));

// Prints: -1
console.log(buf.indexOf(Buffer.from('a buffer example')));

// Prints: 8
console.log(buf.indexOf(Buffer.from('a buffer example').slice(0, 8)));


const utf16Buffer = Buffer.from('\u039a\u0391\u03a3\u03a3\u0395', 'ucs2');

// Prints: 4
console.log(utf16Buffer.indexOf('\u03a3', 0, 'ucs2'));

// Prints: 6
console.log(utf16Buffer.indexOf('\u03a3', -4, 'ucs2'));
```

If `value` is not a string, number, or `Buffer`, this method will throw a
`TypeError`. If `value` is a number, it will be coerced to a valid byte value,
an integer between 0 and 255.

If `byteOffset` is not a number, it will be coerced to a number. Any arguments
that coerce to `NaN` or 0, like `{}`, `[]`, `null` or `undefined`, will search
the whole buffer. This behavior matches [`String#indexOf()`].

```js
const b = Buffer.from('abcdef');

// Passing a value that's a number, but not a valid byte
// Prints: 2, equivalent to searching for 99 or 'c'
console.log(b.indexOf(99.9));
console.log(b.indexOf(256 + 99));

// Passing a byteOffset that coerces to NaN or 0
// Prints: 1, searching the whole buffer
console.log(b.indexOf('b', undefined));
console.log(b.indexOf('b', {}));
console.log(b.indexOf('b', null));
console.log(b.indexOf('b', []));
```

If `value` is an empty string or empty `Buffer` and `byteOffset` is less
than `buf.length`, `byteOffset` will be returned. If `value` is empty and
`byteOffset` is at least `buf.length`, `buf.length` will be returned.

