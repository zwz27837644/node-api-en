<!-- YAML
added: v0.7.2
-->

* {boolean} Set to `false` after `subprocess.disconnect()` is called

The `subprocess.connected` property indicates whether it is still possible to
send and receive messages from a child process. When `subprocess.connected` is
`false`, it is no longer possible to send or receive messages.

<a name="child_process_child_disconnect"></a>
