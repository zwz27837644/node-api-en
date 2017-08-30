<!-- YAML
added: v0.11.12
changes:
  - version: v8.0.0
    pr-url: https://github.com/nodejs/node/pull/10653
    description: The `input` option can now be a `Uint8Array`.
  - version: v6.2.1, v4.5.0
    pr-url: https://github.com/nodejs/node/pull/6939
    description: The `encoding` option can now explicitly be set to `buffer`.
  - version: v5.7.0
    pr-url: https://github.com/nodejs/node/pull/4598
    description: The `shell` option is supported now.
-->

* `command` {string} The command to run
* `args` {Array} List of string arguments
* `options` {Object}
  * `cwd` {string} Current working directory of the child process
  * `input` {string|Buffer|Uint8Array} The value which will be passed as stdin
    to the spawned process
    - supplying this value will override `stdio[0]`
  * `stdio` {string|Array} Child's stdio configuration.
  * `env` {Object} Environment key-value pairs
  * `uid` {number} Sets the user identity of the process. (See setuid(2).)
  * `gid` {number} Sets the group identity of the process. (See setgid(2).)
  * `timeout` {number} In milliseconds the maximum amount of time the process
    is allowed to run. (Default: `undefined`)
  * `killSignal` {string|integer} The signal value to be used when the spawned
    process will be killed. (Default: `'SIGTERM'`)
  * `maxBuffer` {number} Largest amount of data in bytes allowed on stdout or
    stderr. (Default: `200*1024`) If exceeded, the child process is terminated.
    See caveat at [`maxBuffer` and Unicode][].
  * `encoding` {string} The encoding used for all stdio inputs and outputs.
    (Default: `'buffer'`)
  * `shell` {boolean|string} If `true`, runs `command` inside of a shell. Uses
    `'/bin/sh'` on UNIX, and `process.env.ComSpec` on Windows. A different
    shell can be specified as a string. See [Shell Requirements][] and
    [Default Windows Shell][]. Defaults to `false` (no shell).
* Returns: {Object}
  * `pid` {number} Pid of the child process
  * `output` {Array} Array of results from stdio output
  * `stdout` {Buffer|string} The contents of `output[1]`
  * `stderr` {Buffer|string} The contents of `output[2]`
  * `status` {number} The exit code of the child process
  * `signal` {string} The signal used to kill the child process
  * `error` {Error} The error object if the child process failed or timed out

The `child_process.spawnSync()` method is generally identical to
[`child_process.spawn()`][] with the exception that the function will not return
until the child process has fully closed. When a timeout has been encountered
and `killSignal` is sent, the method won't return until the process has
completely exited. Note that if the process intercepts and handles the
`SIGTERM` signal and doesn't exit, the parent process will wait until the child
process has exited.

*Note*: If the `shell` option is enabled, do not pass unsanitised user input
to this function. Any input containing shell metacharacters may be used to
trigger arbitrary command execution.

