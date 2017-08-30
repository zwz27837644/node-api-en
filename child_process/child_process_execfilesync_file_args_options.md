<!-- YAML
added: v0.11.12
changes:
  - version: v8.0.0
    pr-url: https://github.com/nodejs/node/pull/10653
    description: The `input` option can now be a `Uint8Array`.
  - version: v6.2.1, v4.5.0
    pr-url: https://github.com/nodejs/node/pull/6939
    description: The `encoding` option can now explicitly be set to `buffer`.
-->

* `file` {string} The name or path of the executable file to run
* `args` {Array} List of string arguments
* `options` {Object}
  * `cwd` {string} Current working directory of the child process
  * `input` {string|Buffer|Uint8Array} The value which will be passed as stdin
    to the spawned process
    - supplying this value will override `stdio[0]`
  * `stdio` {string|Array} Child's stdio configuration. (Default: `'pipe'`)
    - `stderr` by default will be output to the parent process' stderr unless
      `stdio` is specified
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
  * `encoding` {string} The encoding used for all stdio inputs and outputs. (Default: `'buffer'`)
* Returns: {Buffer|string} The stdout from the command

The `child_process.execFileSync()` method is generally identical to
[`child_process.execFile()`][] with the exception that the method will not return
until the child process has fully closed. When a timeout has been encountered
and `killSignal` is sent, the method won't return until the process has
completely exited.

*Note*: If the child process intercepts and handles the `SIGTERM` signal and
does not exit, the parent process will still wait until the child process has
exited.

If the process times out, or has a non-zero exit code, this method ***will***
throw.  The [`Error`][] object will contain the entire result from
[`child_process.spawnSync()`][]

