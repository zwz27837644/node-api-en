<!-- YAML
added: v0.9.1
-->

* `callback` {Function} The function to call at the end of this turn of
  [the Node.js Event Loop]
* `...args` {any} Optional arguments to pass when the `callback` is called.

Schedules the "immediate" execution of the `callback` after I/O events'
callbacks. Returns an `Immediate` for use with [`clearImmediate()`][].

When multiple calls to `setImmediate()` are made, the `callback` functions are
queued for execution in the order in which they are created. The entire callback
queue is processed every event loop iteration. If an immediate timer is queued
from inside an executing callback, that timer will not be triggered until the
next event loop iteration.

If `callback` is not a function, a [`TypeError`][] will be thrown.

*Note*: This method has a custom variant for promises that is available using
[`util.promisify()`][]:

```js
const util = require('util');
const setImmediatePromise = util.promisify(setImmediate);

setImmediatePromise('foobar').then((value) => {
  // value === 'foobar' (passing values is optional)
  // This is executed after all I/O callbacks.
});

// or with async function
async function timerExample() {
  console.log('Before I/O callbacks');
  await setImmediatePromise();
  console.log('After I/O callbacks');
}
timerExample();
```

