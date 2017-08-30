<!-- YAML
added: v0.9.4
-->

* `encoding` {string} The encoding to use.
* Returns: `this`

The `readable.setEncoding()` method sets the character encoding for
data read from the Readable stream.

By default, no encoding is assigned and stream data will be returned as
`Buffer` objects. Setting an encoding causes the stream data
to be returned as strings of the specified encoding rather than as `Buffer`
objects. For instance, calling `readable.setEncoding('utf8')` will cause the
output data to be interpreted as UTF-8 data, and passed as strings. Calling
`readable.setEncoding('hex')` will cause the data to be encoded in hexadecimal
string format.

The Readable stream will properly handle multi-byte characters delivered through
the stream that would otherwise become improperly decoded if simply pulled from
the stream as `Buffer` objects.

```js
const readable = getReadableStreamSomehow();
readable.setEncoding('utf8');
readable.on('data', (chunk) => {
  assert.equal(typeof chunk, 'string');
  console.log('got %d characters of string data', chunk.length);
});
```

