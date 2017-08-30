<!-- YAML
added: v0.7.1
changes:
  - version: 8.2.0
    pr-url: https://github.com/nodejs/node/pull/14140
    description: The `inspectPort` option is supported now.
  - version: v6.4.0
    pr-url: https://github.com/nodejs/node/pull/7838
    description: The `stdio` option is supported now.
-->

* {Object}
  * `execArgv` {Array} List of string arguments passed to the Node.js
    executable. (Default=`process.execArgv`)
  * `exec` {string} File path to worker file.  (Default=`process.argv[1]`)
  * `args` {Array} String arguments passed to worker.
    (Default=`process.argv.slice(2)`)
  * `silent` {boolean} Whether or not to send output to parent's stdio.
    (Default=`false`)
  * `stdio` {Array} Configures the stdio of forked processes. Because the
    cluster module relies on IPC to function, this configuration must contain an
    `'ipc'` entry. When this option is provided, it overrides `silent`.
  * `uid` {number} Sets the user identity of the process. (See setuid(2).)
  * `gid` {number} Sets the group identity of the process. (See setgid(2).)
  * `inspectPort` {number|function} Sets inspector port of worker.
    This can be a number, or a function that takes no arguments and returns a
    number. By default each worker gets its own port, incremented from the
    master's `process.debugPort`.

After calling `.setupMaster()` (or `.fork()`) this settings object will contain
the settings, including the default values.

This object is not intended to be changed or set manually.

