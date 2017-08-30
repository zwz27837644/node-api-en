
* {Stream}

The `process.stdout` property returns a stream connected to
`stdout` (fd `1`). It is a [`net.Socket`][] (which is a [Duplex][]
stream) unless fd `1` refers to a file, in which case it is
a [Writable][] stream.

For example, to copy process.stdin to process.stdout:

```js
process.stdin.pipe(process.stdout);
```

*Note*: `process.stdout` differs from other Node.js streams in important ways,
see [note on process I/O][] for more information.

