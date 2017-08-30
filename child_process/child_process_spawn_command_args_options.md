<!-- YAML
added: v0.1.90
changes:
  - version: v6.4.0
    pr-url: https://github.com/nodejs/node/pull/7696
    description: The `argv0` option is supported now.
  - version: v5.7.0
    pr-url: https://github.com/nodejs/node/pull/4598
    description: The `shell` option is supported now.
-->

* `command` {string} The command to run
* `args` {Array} List of string arguments
* `options` {Object}
  * `cwd` {string} Current working directory of the child process
  * `env` {Object} Environment key-value pairs
  * `argv0` {string} Explicitly set the value of `argv[0]` sent to the child
    process. This will be set to `command` if not specified.
  * `stdio` {Array|string} Child's stdio configuration. (See
    [`options.stdio`][`stdio`])
  * `detached` {boolean} Prepare child to run independently of its parent
    process. Specific behavior depends on the platform, see
    [`options.detached`][])
  * `uid` {number} Sets the user identity of the process. (See setuid(2).)
  * `gid` {number} Sets the group identity of the process. (See setgid(2).)
  * `shell` {boolean|string} If `true`, runs `command` inside of a shell. Uses
    `'/bin/sh'` on UNIX, and `process.env.ComSpec` on Windows. A different
    shell can be specified as a string. See [Shell Requirements][] and
    [Default Windows Shell][]. Defaults to `false` (no shell).
* Returns: {ChildProcess}

The `child_process.spawn()` method spawns a new process using the given
`command`, with command line arguments in `args`. If omitted, `args` defaults
to an empty array.

*Note*: If the `shell` option is enabled, do not pass unsanitised user input to
this function. Any input containing shell metacharacters may be used to
trigger arbitrary command execution.

A third argument may be used to specify additional options, with these defaults:

```js
const defaults = {
  cwd: undefined,
  env: process.env
};
```

Use `cwd` to specify the working directory from which the process is spawned.
If not given, the default is to inherit the current working directory.

Use `env` to specify environment variables that will be visible to the new
process, the default is [`process.env`][].

Example of running `ls -lh /usr`, capturing `stdout`, `stderr`, and the
exit code:

```js
const { spawn } = require('child_process');
const ls = spawn('ls', ['-lh', '/usr']);

ls.stdout.on('data', (data) => {
  console.log(`stdout: ${data}`);
});

ls.stderr.on('data', (data) => {
  console.log(`stderr: ${data}`);
});

ls.on('close', (code) => {
  console.log(`child process exited with code ${code}`);
});
```


Example: A very elaborate way to run `ps ax | grep ssh`

```js
const { spawn } = require('child_process');
const ps = spawn('ps', ['ax']);
const grep = spawn('grep', ['ssh']);

ps.stdout.on('data', (data) => {
  grep.stdin.write(data);
});

ps.stderr.on('data', (data) => {
  console.log(`ps stderr: ${data}`);
});

ps.on('close', (code) => {
  if (code !== 0) {
    console.log(`ps process exited with code ${code}`);
  }
  grep.stdin.end();
});

grep.stdout.on('data', (data) => {
  console.log(data.toString());
});

grep.stderr.on('data', (data) => {
  console.log(`grep stderr: ${data}`);
});

grep.on('close', (code) => {
  if (code !== 0) {
    console.log(`grep process exited with code ${code}`);
  }
});
```


Example of checking for failed `spawn`:

```js
const { spawn } = require('child_process');
const subprocess = spawn('bad_command');

subprocess.on('error', (err) => {
  console.log('Failed to start subprocess.');
});
```

*Note*: Certain platforms (macOS, Linux) will use the value of `argv[0]` for
the process title while others (Windows, SunOS) will use `command`.

*Note*: Node.js currently overwrites `argv[0]` with `process.execPath` on
startup, so `process.argv[0]` in a Node.js child process will not match the
`argv0` parameter passed to `spawn` from the parent, retrieve it with the
`process.argv0` property instead.

