<!-- YAML
added: v0.9.4
changes:
  - version: v8.0.0
    pr-url: https://github.com/nodejs/node/pull/11608
    description: The `chunk` argument can now be a `Uint8Array` instance.
  - version: v6.0.0
    pr-url: https://github.com/nodejs/node/pull/6170
    description: Passing `null` as the `chunk` parameter will always be
                 considered invalid now, even in object mode.
-->

* `chunk` {string|Buffer|Uint8Array|any} Optional data to write. For streams
  not operating in object mode, `chunk` must be a string, `Buffer` or
  `Uint8Array`. For object mode streams, `chunk` may be any JavaScript value
  other than `null`.
* `encoding` {string} The encoding, if `chunk` is a string
* `callback` {Function} Callback for when this chunk of data is flushed
* Returns: {boolean} `false` if the stream wishes for the calling code to
  wait for the `'drain'` event to be emitted before continuing to write
  additional data; otherwise `true`.

The `writable.write()` method writes some data to the stream, and calls the
supplied `callback` once the data has been fully handled. If an error
occurs, the `callback` *may or may not* be called with the error as its
first argument. To reliably detect write errors, add a listener for the
`'error'` event.

The return value is `true` if the internal buffer is less than the
`highWaterMark` configured when the stream was created after admitting `chunk`.
If `false` is returned, further attempts to write data to the stream should
stop until the [`'drain'`][] event is emitted.

While a stream is not draining, calls to `write()` will buffer `chunk`, and
return false. Once all currently buffered chunks are drained (accepted for
delivery by the operating system), the `'drain'` event will be emitted.
It is recommended that once write() returns false, no more chunks be written
until the `'drain'` event is emitted. While calling `write()` on a stream that
is not draining is allowed, Node.js will buffer all written chunks until
maximum memory usage occurs, at which point it will abort unconditionally.
Even before it aborts, high memory usage will cause poor garbage collector
performance and high RSS (which is not typically released back to the system,
even after the memory is no longer required). Since TCP sockets may never
drain if the remote peer does not read the data, writing a socket that is
not draining may lead to a remotely exploitable vulnerability.

Writing data while the stream is not draining is particularly
problematic for a [Transform][], because the `Transform` streams are paused
by default until they are piped or an `'data'` or `'readable'` event handler
is added.

If the data to be written can be generated or fetched on demand, it is
recommended to encapsulate the logic into a [Readable][] and use
[`stream.pipe()`][]. However, if calling `write()` is preferred, it is
possible to respect backpressure and avoid memory issues using the
[`'drain'`][] event:

```js
function write(data, cb) {
  if (!stream.write(data)) {
    stream.once('drain', cb);
  } else {
    process.nextTick(cb);
  }
}

// Wait for cb to be called before doing any other write.
write('hello', () => {
  console.log('write completed, do more writes now');
});
```

A Writable stream in object mode will always ignore the `encoding` argument.

