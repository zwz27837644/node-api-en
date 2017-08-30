<!-- YAML
added: v0.1.99
-->

The `'message'` event is emitted when a new datagram is available on a socket.
The event handler function is passed two arguments: `msg` and `rinfo`.
* `msg` {Buffer} - The message
* `rinfo` {Object} - Remote address information
  * `address` {string} The sender address
  * `family` {string} The address family (`'IPv4'` or `'IPv6'`)
  * `port` {number} The sender port
  * `size` {number} The message size

