
* {string}

The `error.message` property is the string description of the error as set by
calling `new Error(message)`. The `message` passed to the constructor will also
appear in the first line of the stack trace of the `Error`, however changing
this property after the `Error` object is created *may not* change the first
line of the stack trace (for example, when `error.stack` is read before this
property is changed).

```js
const err = new Error('The message');
console.error(err.message);
// Prints: The message
```

