<!-- YAML
added: v0.1.90
-->

* {number} Integer

Returns the process identifier (PID) of the child process.

Example:

```js
const { spawn } = require('child_process');
const grep = spawn('grep', ['ssh']);

console.log(`Spawned child pid: ${grep.pid}`);
grep.stdin.end();
```

<a name="child_process_child_send_message_sendhandle_options_callback"></a>
