<!-- YAML
added: v0.11.4
-->

* `options` {Object} A set of options providing information for name generation
  * `host` {string} A domain name or IP address of the server to issue the request to
  * `port` {number} Port of remote server
  * `localAddress` {string} Local interface to bind for network connections
    when issuing the request
* Returns: {string}

Get a unique name for a set of request options, to determine whether a
connection can be reused.  For an HTTP agent, this returns
`host:port:localAddress`.  For an HTTPS agent, the name includes the
CA, cert, ciphers, and other HTTPS/TLS-specific options that determine
socket reusability.

