<!-- YAML
added: v0.1.91
-->

* `file` {string} The name or path of the executable file to run
* `args` {Array} List of string arguments
* `options` {Object}
  * `cwd` {string} Current working directory of the child process
  * `env` {Object} Environment key-value pairs
  * `encoding` {string} (Default: `'utf8'`)
  * `timeout` {number} (Default: `0`)
  * `maxBuffer` {number} Largest amount of data in bytes allowed on stdout or
    stderr. (Default: `200*1024`) If exceeded, the child process is terminated.
    See caveat at [`maxBuffer` and Unicode][].
  * `killSignal` {string|integer} (Default: `'SIGTERM'`)
  * `uid` {number} Sets the user identity of the process. (See setuid(2).)
  * `gid` {number} Sets the group identity of the process. (See setgid(2).)
* `callback` {Function} called with the output when process terminates
  * `error` {Error}
  * `stdout` {string|Buffer}
  * `stderr` {string|Buffer}
* Returns: {ChildProcess}

The `child_process.execFile()` function is similar to [`child_process.exec()`][]
except that it does not spawn a shell. Rather, the specified executable `file`
is spawned directly as a new process making it slightly more efficient than
[`child_process.exec()`][].

The same options as [`child_process.exec()`][] are supported. Since a shell is not
spawned, behaviors such as I/O redirection and file globbing are not supported.

```js
const { execFile } = require('child_process');
const child = execFile('node', ['--version'], (error, stdout, stderr) => {
  if (error) {
    throw error;
  }
  console.log(stdout);
});
```

The `stdout` and `stderr` arguments passed to the callback will contain the
stdout and stderr output of the child process. By default, Node.js will decode
the output as UTF-8 and pass strings to the callback. The `encoding` option
can be used to specify the character encoding used to decode the stdout and
stderr output. If `encoding` is `'buffer'`, or an unrecognized character
encoding, `Buffer` objects will be passed to the callback instead.

If this method is invoked as its [`util.promisify()`][]ed version, it returns
a Promise for an object with `stdout` and `stderr` properties. In case of an
error, a rejected promise is returned, with the same `error` object given in the
callback, but with an additional two properties `stdout` and `stderr`.

```js
const util = require('util');
const execFile = util.promisify(require('child_process').execFile);
async function getVersion() {
  const { stdout } = await execFile('node', ['--version']);
  console.log(stdout);
}
getVersion();
```

