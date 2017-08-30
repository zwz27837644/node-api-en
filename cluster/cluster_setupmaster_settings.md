<!-- YAML
added: v0.7.1
changes:
  - version: v6.4.0
    pr-url: https://github.com/nodejs/node/pull/7838
    description: The `stdio` option is supported now.
-->

* `settings` {Object} see [`cluster.settings`][]

`setupMaster` is used to change the default 'fork' behavior. Once called,
the settings will be present in `cluster.settings`.

Note that:

* Any settings changes only affect future calls to `.fork()` and have no
  effect on workers that are already running.
* The *only* attribute of a worker that cannot be set via `.setupMaster()` is
  the `env` passed to `.fork()`.
* The defaults above apply to the first call only, the defaults for later
  calls is the current value at the time of `cluster.setupMaster()` is called.

Example:

```js
const cluster = require('cluster');
cluster.setupMaster({
  exec: 'worker.js',
  args: ['--use', 'https'],
  silent: true
});
cluster.fork(); // https worker
cluster.setupMaster({
  exec: 'worker.js',
  args: ['--use', 'http']
});
cluster.fork(); // http worker
```

This can only be called from the master process.

