<!-- YAML
changes:
  - version: v8.0.0
    pr-url: https://github.com/nodejs/node/pull/9744
    description: Errors that occur while writing to the underlying streams
                 will now be ignored.
-->

<!--type=class-->

The `Console` class can be used to create a simple logger with configurable
output streams and can be accessed using either `require('console').Console`
or `console.Console` (or their destructured counterparts):

```js
const { Console } = require('console');
```

```js
const { Console } = console;
```

