
A subclass of `Error` that indicates that an attempt is being made to access a
variable that is not defined. Such errors commonly indicate typos in code, or
an otherwise broken program.

While client code may generate and propagate these errors, in practice, only V8
will do so.

```js
doesNotExist;
// throws ReferenceError, doesNotExist is not a variable in this program.
```

Unless an application is dynamically generating and running code,
`ReferenceError` instances should always be considered a bug in the code
or its dependencies.

