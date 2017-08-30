<!-- YAML
added: v0.1.91
changes:
  - version: v5.8.0
    pr-url: https://github.com/nodejs/node/pull/5388
    description: The `options` parameter is optional now.
-->

* `options` {Object|string}
  * `prompt` {string} The input prompt to display. Defaults to `> `
    (with a trailing space).
  * `input` {Readable} The Readable stream from which REPL input will be read.
    Defaults to `process.stdin`.
  * `output` {Writable} The Writable stream to which REPL output will be
    written. Defaults to `process.stdout`.
  * `terminal` {boolean} If `true`, specifies that the `output` should be
    treated as a a TTY terminal, and have ANSI/VT100 escape codes written to it.
    Defaults to checking the value of the `isTTY` property on the `output`
    stream upon instantiation.
  * `eval` {Function} The function to be used when evaluating each given line
    of input. Defaults to an async wrapper for the JavaScript `eval()`
    function.  An `eval` function can error with `repl.Recoverable` to indicate
    the input was incomplete and prompt for additional lines.
  * `useColors` {boolean} If `true`, specifies that the default `writer`
    function should include ANSI color styling to REPL output. If a custom
    `writer` function is provided then this has no effect. Defaults to the
     REPL instances `terminal` value.
  * `useGlobal` {boolean} If `true`, specifies that the default evaluation
     function will use the JavaScript `global` as the context as opposed to
     creating a new separate context for the REPL instance. The node CLI REPL
     sets this value to `true`. Defaults to `false`.
  * `ignoreUndefined` {boolean} If `true`, specifies that the default writer
     will not output the return value of a command if it evaluates to
     `undefined`. Defaults to `false`.
  * `writer` {Function} The function to invoke to format the output of each
     command before writing to `output`. Defaults to [`util.inspect()`][].
  * `completer` {Function} An optional function used for custom Tab auto
     completion. See [`readline.InterfaceCompleter`][] for an example.
  * `replMode` {symbol} A flag that specifies whether the default evaluator
    executes all JavaScript commands in strict mode or default (sloppy) mode.
    Acceptable values are:
    * `repl.REPL_MODE_SLOPPY` - evaluates expressions in sloppy mode.
    * `repl.REPL_MODE_STRICT` - evaluates expressions in strict mode. This is
      equivalent to prefacing every repl statement with `'use strict'`.
    * `repl.REPL_MODE_MAGIC` - This value is **deprecated**, since enhanced
      spec compliance in V8 has rendered magic mode unnecessary. It is now
      equivalent to `repl.REPL_MODE_SLOPPY` (documented above).
  * `breakEvalOnSigint` - Stop evaluating the current piece of code when
    `SIGINT` is received, i.e. `Ctrl+C` is pressed. This cannot be used together
    with a custom `eval` function. Defaults to `false`.

The `repl.start()` method creates and starts a `repl.REPLServer` instance.

If `options` is a string, then it specifies the input prompt:

```js
const repl = require('repl');

// a Unix style prompt
repl.start('$ ');
```

