
For the following cases, consider using ES2015 [`Object.is()`][],
which uses the [SameValueZero][] comparison.

```js
const a = 0;
const b = -a;
assert.notStrictEqual(a, b);
// AssertionError: 0 !== -0
// Strict Equality Comparison doesn't distinguish between -0 and +0...
assert(!Object.is(a, b));
// but Object.is() does!

const str1 = 'foo';
const str2 = 'foo';
assert.strictEqual(str1 / 1, str2 / 1);
// AssertionError: NaN === NaN
// Strict Equality Comparison can't be used to check NaN...
assert(Object.is(str1 / 1, str2 / 1));
// but Object.is() can!
```

For more information, see
[MDN's guide on equality comparisons and sameness][mdn-equality-guide].

[`Error`]: errors.html#errors_class_error
[`Error.captureStackTrace`]: errors.html#errors_error_capturestacktrace_targetobject_constructoropt
[`Map`]: https://developer.mozilla.org/en/docs/Web/JavaScript/Reference/Global_Objects/Map
[`Object.is()`]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/is
[`RegExp`]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Regular_Expressions
[`Set`]: https://developer.mozilla.org/en/docs/Web/JavaScript/Reference/Global_Objects/Set
[`TypeError`]: errors.html#errors_class_typeerror
[`assert.deepEqual()`]: #assert_assert_deepequal_actual_expected_message
[`assert.deepStrictEqual()`]: #assert_assert_deepstrictequal_actual_expected_message
[`assert.ok()`]: #assert_assert_ok_value_message
[`assert.throws()`]: #assert_assert_throws_block_error_message
[Abstract Equality Comparison]: https://tc39.github.io/ecma262/#sec-abstract-equality-comparison
[Object.prototype.toString()]: https://tc39.github.io/ecma262/#sec-object.prototype.tostring
[SameValueZero]: https://tc39.github.io/ecma262/#sec-samevaluezero
[Strict Equality Comparison]: https://tc39.github.io/ecma262/#sec-strict-equality-comparison
[caveats]: #assert_caveats
[enumerable "own" properties]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Enumerability_and_ownership_of_properties
[mdn-equality-guide]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Equality_comparisons_and_sameness
[prototype-spec]: https://tc39.github.io/ecma262/#sec-ordinary-object-internal-methods-and-internal-slots
[Object wrappers]: https://developer.mozilla.org/en-US/docs/Glossary/Primitive#Primitive_wrapper_objects_in_JavaScript
