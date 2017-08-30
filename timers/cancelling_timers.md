
The [`setImmediate()`][], [`setInterval()`][], and [`setTimeout()`][] methods
each return objects that represent the scheduled timers. These can be used to
cancel the timer and prevent it from triggering.

It is not possible to cancel timers that were created using the promisified
variants of [`setImmediate()`][], [`setTimeout()`][].

