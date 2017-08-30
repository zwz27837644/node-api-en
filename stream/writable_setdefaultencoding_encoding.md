<!-- YAML
added: v0.11.15
changes:
  - version: v6.1.0
    pr-url: https://github.com/nodejs/node/pull/5040
    description: This method now returns a reference to `writable`.
-->

* `encoding` {string} The new default encoding
* Returns: `this`

The `writable.setDefaultEncoding()` method sets the default `encoding` for a
[Writable][] stream.

