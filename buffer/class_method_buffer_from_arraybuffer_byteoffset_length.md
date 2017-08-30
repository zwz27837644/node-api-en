<!-- YAML
added: v5.10.0
-->

* `arrayBuffer` {ArrayBuffer} An [`ArrayBuffer`] or the `.buffer` property of a
  [`TypedArray`].
* `byteOffset` {integer} Index of first byte to expose. **Default:** `0`
* `length` {integer} Number of bytes to expose.
  **Default:** `arrayBuffer.length - byteOffset`

This creates a view of the [`ArrayBuffer`] without copying the underlying
memory. For example, when passed a reference to the `.buffer` property of a
[`TypedArray`] instance, the newly created `Buffer` will share the same
allocated memory as the [`TypedArray`].

Example:

```js
const arr = new Uint16Array(2);

arr[0] = 5000;
arr[1] = 4000;

// Shares memory with `arr`
const buf = Buffer.from(arr.buffer);

// Prints: <Buffer 88 13 a0 0f>
console.log(buf);

// Changing the original Uint16Array changes the Buffer also
arr[1] = 6000;

// Prints: <Buffer 88 13 70 17>
console.log(buf);
```

The optional `byteOffset` and `length` arguments specify a memory range within
the `arrayBuffer` that will be shared by the `Buffer`.

Example:

```js
const ab = new ArrayBuffer(10);
const buf = Buffer.from(ab, 0, 2);

// Prints: 2
console.log(buf.length);
```

A `TypeError` will be thrown if `arrayBuffer` is not an [`ArrayBuffer`].

