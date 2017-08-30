<!-- YAML
added: v0.1.90
-->

* `string` {string} String to be written to `buf`
* `offset` {integer} Where to start writing `string`. **Default:** `0`
* `length` {integer} How many bytes to write. **Default:** `buf.length - offset`
* `encoding` {string} The character encoding of `string`. **Default:** `'utf8'`
* Returns: {integer} Number of bytes written

Writes `string` to `buf` at `offset` according to the character encoding in `encoding`.
The `length` parameter is the number of bytes to write. If `buf` did not contain
enough space to fit the entire string, only a partial amount of `string` will
be written. However, partially encoded characters will not be written.

Example:

```js
const buf = Buffer.allocUnsafe(256);

const len = buf.write('\u00bd + \u00bc = \u00be', 0);

// Prints: 12 bytes: ½ + ¼ = ¾
console.log(`${len} bytes: ${buf.toString('utf8', 0, len)}`);
```

