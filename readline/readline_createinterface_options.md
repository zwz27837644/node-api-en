<!-- YAML
added: v0.1.98
changes:
  - version: v6.3.0
    pr-url: https://github.com/nodejs/node/pull/7125
    description: The `prompt` option is supported now.
  - version: v6.0.0
    pr-url: https://github.com/nodejs/node/pull/6352
    description: The `historySize` option can be `0` now.
-->

* `options` {Object}
  * `input` {Readable} The [Readable][] stream to listen to. This option is
    *required*.
  * `output` {Writable} The [Writable][] stream to write readline data to.
  * `completer` {Function} An optional function used for Tab autocompletion.
  * `terminal` {boolean} `true` if the `input` and `output` streams should be
    treated like a TTY, and have ANSI/VT100 escape codes written to it.
    Defaults to checking `isTTY` on the `output` stream upon instantiation.
  * `historySize` {number} maximum number of history lines retained. To disable
    the history set this value to `0`. Defaults to `30`. This option makes sense
    only if `terminal` is set to `true` by the user or by an internal `output`
    check, otherwise the history caching mechanism is not initialized at all.
  * `prompt` - the prompt string to use. Default: `'> '`
  * `crlfDelay` {number} If the delay between `\r` and `\n` exceeds
    `crlfDelay` milliseconds, both `\r` and `\n` will be treated as separate
    end-of-line input. Default to `100` milliseconds.
    `crlfDelay` will be coerced to a number no less than `100`. It can be set to
    `Infinity`, in which case `\r` followed by `\n` will always be considered a
    single newline.
  * `removeHistoryDuplicates` {boolean} If `true`, when a new input line added
    to the history list duplicates an older one, this removes the older line
    from the list. Defaults to `false`.

The `readline.createInterface()` method creates a new `readline.Interface`
instance.

For example:

```js
const readline = require('readline');
const rl = readline.createInterface({
  input: process.stdin,
  output: process.stdout
});
```

Once the `readline.Interface` instance is created, the most common case is to
listen for the `'line'` event:

```js
rl.on('line', (line) => {
  console.log(`Received: ${line}`);
});
```

If `terminal` is `true` for this instance then the `output` stream will get
the best compatibility if it defines an `output.columns` property and emits
a `'resize'` event on the `output` if or when the columns ever change
([`process.stdout`][] does this automatically when it is a TTY).

