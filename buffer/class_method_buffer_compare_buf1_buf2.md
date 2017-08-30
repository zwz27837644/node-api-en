<!-- YAML
added: v0.11.13
changes:
  - version: v8.0.0
    pr-url: https://github.com/nodejs/node/pull/10236
    description: The arguments can now be `Uint8Array`s.
-->

* `buf1` {Buffer|Uint8Array}
* `buf2` {Buffer|Uint8Array}
* Returns: {integer}

Compares `buf1` to `buf2` typically for the purpose of sorting arrays of
`Buffer` instances. This is equivalent to calling
[`buf1.compare(buf2)`][`buf.compare()`].

Example:

```js
const buf1 = Buffer.from('1234');
const buf2 = Buffer.from('0123');
const arr = [buf1, buf2];

// Prints: [ <Buffer 30 31 32 33>, <Buffer 31 32 33 34> ]
// (This result is equal to: [buf2, buf1])
console.log(arr.sort(Buffer.compare));
```

