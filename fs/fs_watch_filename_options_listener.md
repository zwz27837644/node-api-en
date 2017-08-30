<!-- YAML
added: v0.5.10
changes:
  - version: v7.6.0
    pr-url: https://github.com/nodejs/node/pull/10739
    description: The `filename` parameter can be a WHATWG `URL` object using
                 `file:` protocol. Support is currently still *experimental*.
  - version: v7.0.0
    pr-url: https://github.com/nodejs/node/pull/7831
    description: The passed `options` object will never be modified.
-->

* `filename` {string|Buffer|URL}
* `options` {string|Object}
  * `persistent` {boolean} Indicates whether the process should continue to run
    as long as files are being watched. **Default:** `true`
  * `recursive` {boolean} Indicates whether all subdirectories should be
    watched, or only the current directory. This applies when a directory is
    specified, and only on supported platforms (See [Caveats][]). **Default:**
    `false`
  * `encoding` {string} Specifies the character encoding to be used for the
     filename passed to the listener. **Default:** `'utf8'`
* `listener` {Function|undefined} **Default:** `undefined`

Watch for changes on `filename`, where `filename` is either a file or a
directory.  The returned object is a [`fs.FSWatcher`][].

The second argument is optional. If `options` is provided as a string, it
specifies the `encoding`. Otherwise `options` should be passed as an object.

The listener callback gets two arguments `(eventType, filename)`.  `eventType` is either
`'rename'` or `'change'`, and `filename` is the name of the file which triggered
the event.

Note that on most platforms, `'rename'` is emitted whenever a filename appears
or disappears in the directory.

Also note the listener callback is attached to the `'change'` event fired by
[`fs.FSWatcher`][], but it is not the same thing as the `'change'` value of
`eventType`.

