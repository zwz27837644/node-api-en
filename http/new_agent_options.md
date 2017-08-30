<!-- YAML
added: v0.3.4
-->

* `options` {Object} Set of configurable options to set on the agent.
  Can have the following fields:
  * `keepAlive` {boolean} Keep sockets around even when there are no
    outstanding requests, so they can be used for future requests without
    having to reestablish a TCP connection. Defaults to `false`
  * `keepAliveMsecs` {number} When using the `keepAlive` option, specifies
    the [initial delay](net.html#net_socket_setkeepalive_enable_initialdelay)
    for TCP Keep-Alive packets. Ignored when the
    `keepAlive` option is `false` or `undefined`. Defaults to `1000`.
  * `maxSockets` {number} Maximum number of sockets to allow per
    host.  Defaults to `Infinity`.
  * `maxFreeSockets` {number} Maximum number of sockets to leave open
    in a free state.  Only relevant if `keepAlive` is set to `true`.
    Defaults to `256`.

The default [`http.globalAgent`][] that is used by [`http.request()`][] has all
of these values set to their respective defaults.

To configure any of them, a custom [`http.Agent`][] instance must be created.

```js
const http = require('http');
const keepAliveAgent = new http.Agent({ keepAlive: true });
options.agent = keepAliveAgent;
http.request(options, onResponseCallback);
```

