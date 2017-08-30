
The "two modes" of operation for a Readable stream are a simplified abstraction
for the more complicated internal state management that is happening within the
Readable stream implementation.

Specifically, at any given point in time, every Readable is in one of three
possible states:

* `readable._readableState.flowing = null`
* `readable._readableState.flowing = false`
* `readable._readableState.flowing = true`

When `readable._readableState.flowing` is `null`, no mechanism for consuming the
streams data is provided so the stream will not generate its data. While in this
state, attaching a listener for the `'data'` event, calling the `readable.pipe()`
method, or calling the `readable.resume()` method will switch
`readable._readableState.flowing` to `true`, causing the Readable to begin
actively emitting events as data is generated.

Calling `readable.pause()`, `readable.unpipe()`, or receiving "back pressure"
will cause the `readable._readableState.flowing` to be set as `false`,
temporarily halting the flowing of events but *not* halting the generation of
data. While in this state, attaching a listener for the `'data'` event
would not cause `readable._readableState.flowing` to switch to `true`.

```js
const { PassThrough, Writable } = require('stream');
const pass = new PassThrough();
const writable = new Writable();

pass.pipe(writable);
pass.unpipe(writable);
// flowing is now false

pass.on('data', (chunk) => { console.log(chunk.toString()); });
pass.write('ok'); // will not emit 'data'
pass.resume(); // must be called to make 'data' being emitted
```

While `readable._readableState.flowing` is `false`, data may be accumulating
within the streams internal buffer.

