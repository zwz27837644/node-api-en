<!-- YAML
added: v0.1.90
-->

* `command` {string} The command to run, with space-separated arguments
* `options` {Object}
  * `cwd` {string} Current working directory of the child process
  * `env` {Object} Environment key-value pairs
  * `encoding` {string} (Default: `'utf8'`)
  * `shell` {string} Shell to execute the command with
    (Default: `'/bin/sh'` on UNIX, `process.env.ComSpec` on Windows. See
    [Shell Requirements][] and [Default Windows Shell][].)
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

Spawns a shell then executes the `command` within that shell, buffering any
generated output. The `command` string passed to the exec function is processed
directly by the shell and special characters (vary based on
[shell](https://en.wikipedia.org/wiki/List_of_command-line_interpreters))
need to be dealt with accordingly:
```js
exec('"/path/to/test file/test.sh" arg1 arg2');
//Double quotes are used so that the space in the path is not interpreted as
//multiple arguments

exec('echo "The \\$HOME variable is $HOME"');
//The $HOME variable is escaped in the first instance, but not in the second
```

*Note*: Never pass unsanitised user input to this function. Any input
containing shell metacharacters may be used to trigger arbitrary command
execution.

```js
const { exec } = require('child_process');
exec('cat *.js bad_file | wc -l', (error, stdout, stderr) => {
  if (error) {
    console.error(`exec error: ${error}`);
    return;
  }
  console.log(`stdout: ${stdout}`);
  console.log(`stderr: ${stderr}`);
});
```

If a `callback` function is provided, it is called with the arguments
`(error, stdout, stderr)`. On success, `error` will be `null`.  On error,
`error` will be an instance of [`Error`][]. The `error.code` property will be
the exit code of the child process while `error.signal` will be set to the
signal that terminated the process. Any exit code other than `0` is considered
to be an error.

The `stdout` and `stderr` arguments passed to the callback will contain the
stdout and stderr output of the child process. By default, Node.js will decode
the output as UTF-8 and pass strings to the callback. The `encoding` option
can be used to specify the character encoding used to decode the stdout and
stderr output. If `encoding` is `'buffer'`, or an unrecognized character
encoding, `Buffer` objects will be passed to the callback instead.

The `options` argument may be passed as the second argument to customize how
the process is spawned. The default options are:

```js
const defaults = {
  encoding: 'utf8',
  timeout: 0,
  maxBuffer: 200 * 1024,
  killSignal: 'SIGTERM',
  cwd: null,
  env: null
};
```

If `timeout` is greater than `0`, the parent will send the signal
identified by the `killSignal` property (the default is `'SIGTERM'`) if the
child runs longer than `timeout` milliseconds.

*Note*: Unlike the exec(3) POSIX system call, `child_process.exec()` does not
replace the existing process and uses a shell to execute the command.

If this method is invoked as its [`util.promisify()`][]ed version, it returns
a Promise for an object with `stdout` and `stderr` properties. In case of an
error, a rejected promise is returned, with the same `error` object given in the
callback, but with an additional two properties `stdout` and `stderr`.

For example:

```js
const util = require('util');
const exec = util.promisify(require('child_process').exec);

async function lsExample() {
  const { stdout, stderr } = await exec('ls');
  console.log('stdout:', stdout);
  console.log('stderr:', stderr);
}
lsExample();
```

