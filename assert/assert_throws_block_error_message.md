<!-- YAML
added: v0.1.21
changes:
  - version: v4.2.0
    pr-url: https://github.com/nodejs/node/pull/3276
    description: The `error` parameter can now be an arrow function.
-->
* `block` {Function}
* `error` {RegExp|Function}
* `message` {any}

Expects the function `block` to throw an error.

If specified, `error` can be a constructor, [`RegExp`][], or validation
function.

If specified, `message` will be the message provided by the `AssertionError` if
the block fails to throw.

Validate instanceof using constructor:

```js
assert.throws(
  () => {
    throw new Error('Wrong value');
  },
  Error
);
```

Validate error message using [`RegExp`][]:

```js
assert.throws(
  () => {
    throw new Error('Wrong value');
  },
  /value/
);
```

Custom error validation:

```js
assert.throws(
  () => {
    throw new Error('Wrong value');
  },
  function(err) {
    if ((err instanceof Error) && /value/.test(err)) {
      return true;
    }
  },
  'unexpected error'
);
```

Note that `error` can not be a string. If a string is provided as the second
argument, then `error` is assumed to be omitted and the string will be used for
`message` instead. This can lead to easy-to-miss mistakes:

<!-- eslint-disable no-restricted-syntax -->
```js
// THIS IS A MISTAKE! DO NOT DO THIS!
assert.throws(myFunction, 'missing foo', 'did not throw with expected message');

// Do this instead.
assert.throws(myFunction, /missing foo/, 'did not throw with expected message');
```

