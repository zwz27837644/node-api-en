
A common use case for `readline` is to consume input from a filesystem
[Readable][] stream one line at a time, as illustrated in the following
example:

```js
const readline = require('readline');
const fs = require('fs');

const rl = readline.createInterface({
  input: fs.createReadStream('sample.txt')
});

rl.on('line', (line) => {
  console.log(`Line from file: ${line}`);
});
```

[`SIGCONT`]: readline.html#readline_event_sigcont
[`SIGTSTP`]: readline.html#readline_event_sigtstp
[`process.stdin`]: process.html#process_process_stdin
[`process.stdout`]: process.html#process_process_stdout
[Readable]: stream.html#stream_readable_streams
[TTY]: tty.html
[Writable]: stream.html#stream_writable_streams
