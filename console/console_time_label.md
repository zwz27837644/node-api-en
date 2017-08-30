<!-- YAML
added: v0.1.104
-->
* `label` {string}

Starts a timer that can be used to compute the duration of an operation. Timers
are identified by a unique `label`. Use the same `label` when calling
[`console.timeEnd()`][] to stop the timer and output the elapsed time in
milliseconds to `stdout`. Timer durations are accurate to the sub-millisecond.

