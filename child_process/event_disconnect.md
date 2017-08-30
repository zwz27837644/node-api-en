<!-- YAML
added: v0.7.2
-->

The `'disconnect'` event is emitted after calling the
[`subprocess.disconnect()`][] method in parent process or
[`process.disconnect()`][] in child process. After disconnecting it is no longer
possible to send or receive messages, and the [`subprocess.connected`][]
property is `false`.

