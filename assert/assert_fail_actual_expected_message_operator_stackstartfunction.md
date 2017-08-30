<!-- YAML
added: v0.1.21
-->
* `actual` {any}
* `expected` {any}
* `message` {any}
* `operator` {string} (default: '!=')
* `stackStartFunction` {function} (default: `assert.fail`)

Throws an `AssertionError`. If `message` is falsy, the error message is set as
the values of `actual` and `expected` separated by the provided `operator`.
If just the two `actual` and `expected` arguments are provided, `operator` will
default to `'!='`. If `message` is provided only it will be used as the error
message, the other arguments will be stored as properties on the thrown object.
If `stackStartFunction` is provided, all stack frames above that function will
be removed from stacktrace (see [`Error.captureStackTrace`]).

```js
const assert = require('assert');

assert.fail(1, 2, undefined, '>');
// AssertionError [ERR_ASSERTION]: 1 > 2

assert.fail(1, 2, 'fail');
// AssertionError [ERR_ASSERTION]: fail

assert.fail(1, 2, 'whoops', '>');
// AssertionError [ERR_ASSERTION]: whoops
```

*Note*: Is the last two cases `actual`, `expected`, and `operator` have no
influence on the error message.

```js
assert.fail();
// AssertionError [ERR_ASSERTION]: Failed

assert.fail('boom');
// AssertionError [ERR_ASSERTION]: boom

assert.fail('a', 'b');
// AssertionError [ERR_ASSERTION]: 'a' != 'b'
```

Example use of `stackStartFunction` for truncating the exception's stacktrace:
```js
function suppressFrame() {
  assert.fail('a', 'b', undefined, '!==', suppressFrame);
}
suppressFrame();
// AssertionError [ERR_ASSERTION]: 'a' !== 'b'
//     at repl:1:1
//     at ContextifyScript.Script.runInThisContext (vm.js:44:33)
//     ...
```

