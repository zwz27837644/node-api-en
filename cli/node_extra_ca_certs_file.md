<!-- YAML
added: v7.3.0
-->

When set, the well known "root" CAs (like VeriSign) will be extended with the
extra certificates in `file`. The file should consist of one or more trusted
certificates in PEM format. A message will be emitted (once) with
[`process.emitWarning()`][emit_warning] if the file is missing or
malformed, but any errors are otherwise ignored.

Note that neither the well known nor extra certificates are used when the `ca`
options property is explicitly specified for a TLS or HTTPS client or server.

