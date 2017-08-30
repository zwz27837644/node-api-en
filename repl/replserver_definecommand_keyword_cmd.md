<!-- YAML
added: v0.3.0
-->

* `keyword` {string} The command keyword (*without* a leading `.` character).
* `cmd` {Object|Function} The function to invoke when the command is processed.

The `replServer.defineCommand()` method is used to add new `.`-prefixed commands
to the REPL instance. Such commands are invoked by typing a `.` followed by the
`keyword`. The `cmd` is either a Function or an object with the following
properties:

* `help` {string} Help text to be displayed when `.help` is entered (Optional).
* `action` {Function} The function to execute, optionally accepting a single
  string argument.

The following example shows two new commands added to the REPL instance:

```js
const repl = require('repl');

const replServer = repl.start({ prompt: '> ' });
replServer.defineCommand('sayhello', {
  help: 'Say hello',
  action(name) {
    this.bufferedCommand = '';
    console.log(`Hello, ${name}!`);
    this.displayPrompt();
  }
});
replServer.defineCommand('saybye', function saybye() {
  console.log('Goodbye!');
  this.close();
});
```

The new commands can then be used from within the REPL instance:

```txt
> .sayhello Node.js User
Hello, Node.js User!
> .saybye
Goodbye!
```

