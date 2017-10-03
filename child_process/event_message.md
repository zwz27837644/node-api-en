<!-- YAML
added: v0.5.9
-->

* `message` {Object} a parsed JSON object or primitive value.
* `sendHandle` {Handle} a [`net.Socket`][] or [`net.Server`][] object, or
  undefined.

The `'message'` event is triggered when a child process uses [`process.send()`][]
to send messages.

*Note*: The message goes through JSON serialization and parsing. The resulting
message might not be the same as what is originally sent. See notes in
[the `JSON.stringify()` specification][`JSON.stringify` spec].

<a name="child_process_child_channel"></a>
