<!-- YAML
added: v0.1.90
changes:
  - version: v7.0.0
    pr-url: https://github.com/nodejs/node/pull/8946
    description: Passing invalid input will now throw an error.
  - version: v5.10.0
    pr-url: https://github.com/nodejs/node/pull/5255
    description: The `string` parameter can now be any `TypedArray`, `DataView`
                 or `ArrayBuffer`.
-->

* `string` {string|Buffer|TypedArray|DataView|ArrayBuffer} A value to
  calculate the length of
* `encoding` {string} If `string` is a string, this is its encoding.
  **Default:** `'utf8'`
* Returns: {integer} The number of bytes contained within `string`

Returns the actual byte length of a string. This is not the same as
[`String.prototype.length`] since that returns the number of *characters* in
a string.

*Note*: For `'base64'` and `'hex'`, this function assumes valid input. For
strings that contain non-Base64/Hex-encoded data (e.g. whitespace), the return
value might be greater than the length of a `Buffer` created from the string.

Example:

```js
const str = '\u00bd + \u00bc = \u00be';

// Prints: ½ + ¼ = ¾: 9 characters, 12 bytes
console.log(`${str}: ${str.length} characters, ` +
            `${Buffer.byteLength(str, 'utf8')} bytes`);
```

When `string` is a `Buffer`/[`DataView`]/[`TypedArray`]/[`ArrayBuffer`], the
actual byte length is returned.

