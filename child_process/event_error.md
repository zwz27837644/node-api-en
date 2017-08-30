
* `err` {Error} the error.

The `'error'` event is emitted whenever:

1. The process could not be spawned, or
2. The process could not be killed, or
3. Sending a message to the child process failed.

*Note*: The `'exit'` event may or may not fire after an error has occurred.
When listening to both the `'exit'` and `'error'` events, it is important
to guard against accidentally invoking handler functions multiple times.

See also [`subprocess.kill()`][] and [`subprocess.send()`][].

