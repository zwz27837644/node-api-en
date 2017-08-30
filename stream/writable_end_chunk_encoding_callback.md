<!-- YAML
added: v0.9.4
changes:
  - version: v8.0.0
    pr-url: https://github.com/nodejs/node/pull/11608
    description: The `chunk` argument can now be a `Uint8Array` instance.
-->

* `chunk` {string|Buffer|Uint8Array|any} Optional data to write. For streams
  not operating in object mode, `chunk` must be a string, `Buffer` or
  `Uint8Array`. For object mode streams, `chunk` may be any JavaScript value
  other than `null`.
* `encoding` {string} The encoding, if `chunk` is a string
* `callback` {Function} Optional callback for when the stream is finished

Calling the `writable.end()` method signals that no more data will be written
to the [Writable][]. The optional `chunk` and `encoding` arguments allow one
final additional chunk of data to be written immediately before closing the
stream. If provided, the optional `callback` function is attached as a listener
for the [`'finish'`][] event.

Calling the [`stream.write()`][stream-write] method after calling
[`stream.end()`][stream-end] will raise an error.

```js
// write 'hello, ' and then end with 'world!'
const file = fs.createWriteStream('example.txt');
file.write('hello, ');
file.end('world!');
// writing more now is not allowed!
```

