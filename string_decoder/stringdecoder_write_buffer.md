<!-- YAML
added: v0.1.99
changes:
  - version: v8.0.0
    pr-url: https://github.com/nodejs/node/pull/9618
    description: Each invalid character is now replaced by a single replacement
                 character instead of one for each individual byte.
-->

* `buffer` {Buffer} A `Buffer` containing the bytes to decode.

Returns a decoded string, ensuring that any incomplete multibyte characters at
the end of the `Buffer` are omitted from the returned string and stored in an
internal buffer for the next call to `stringDecoder.write()` or
`stringDecoder.end()`.
