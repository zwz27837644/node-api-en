<!-- YAML
added: v0.9.12
-->

* {number} Timeout in milliseconds. Defaults to 120000 (2 minutes).

The number of milliseconds of inactivity before a socket is presumed
to have timed out.

A value of 0 will disable the timeout behavior on incoming connections.

*Note*: The socket timeout logic is set up on connection, so changing this
value only affects new connections to the server, not any existing connections.

