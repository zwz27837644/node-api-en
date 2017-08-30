<!-- YAML
added: v0.3.6
changes:
  - version: v7.5.0
    pr-url: https://github.com/nodejs/node/pull/10638
    description: The `options` parameter can be a WHATWG `URL` object.
-->
- `options` {Object | string | URL} Accepts all `options` from [`http.request()`][],
  with some differences in default values:
  - `protocol` Defaults to `https:`
  - `port` Defaults to `443`.
  - `agent` Defaults to `https.globalAgent`.
- `callback` {Function}


Makes a request to a secure web server.

The following additional `options` from [`tls.connect()`][] are also accepted when using a
  custom [`Agent`][]:
  `pfx`, `key`, `passphrase`, `cert`, `ca`, `ciphers`, `rejectUnauthorized`, `secureProtocol`, `servername`

`options` can be an object, a string, or a [`URL`][] object. If `options` is a
string, it is automatically parsed with [`url.parse()`][]. If it is a [`URL`][]
object, it will be automatically converted to an ordinary `options` object.

Example:

```js
const https = require('https');

const options = {
  hostname: 'encrypted.google.com',
  port: 443,
  path: '/',
  method: 'GET'
};

const req = https.request(options, (res) => {
  console.log('statusCode:', res.statusCode);
  console.log('headers:', res.headers);

  res.on('data', (d) => {
    process.stdout.write(d);
  });
});

req.on('error', (e) => {
  console.error(e);
});
req.end();
```
Example using options from [`tls.connect()`][]:

```js
const options = {
  hostname: 'encrypted.google.com',
  port: 443,
  path: '/',
  method: 'GET',
  key: fs.readFileSync('test/fixtures/keys/agent2-key.pem'),
  cert: fs.readFileSync('test/fixtures/keys/agent2-cert.pem')
};
options.agent = new https.Agent(options);

const req = https.request(options, (res) => {
  // ...
});
```

Alternatively, opt out of connection pooling by not using an `Agent`.

Example:

```js
const options = {
  hostname: 'encrypted.google.com',
  port: 443,
  path: '/',
  method: 'GET',
  key: fs.readFileSync('test/fixtures/keys/agent2-key.pem'),
  cert: fs.readFileSync('test/fixtures/keys/agent2-cert.pem'),
  agent: false
};

const req = https.request(options, (res) => {
  // ...
});
```

Example using a [`URL`][] as `options`:

```js
const { URL } = require('url');

const options = new URL('https://abc:xyz@example.com');

const req = https.request(options, (res) => {
  // ...
});
```

[`Agent`]: #https_class_https_agent
[`URL`]: url.html#url_the_whatwg_url_api
[`http.Agent`]: http.html#http_class_http_agent
[`http.Server#keepAliveTimeout`]: http.html#http_server_keepalivetimeout
[`http.Server#setTimeout()`]: http.html#http_server_settimeout_msecs_callback
[`http.Server#timeout`]: http.html#http_server_timeout
[`http.Server`]: http.html#http_class_http_server
[`http.close()`]: http.html#http_server_close_callback
[`http.get()`]: http.html#http_http_get_options_callback
[`http.listen()`]: http.html#http_server_listen_port_hostname_backlog_callback
[`http.request()`]: http.html#http_http_request_options_callback
[`https.Agent`]: #https_class_https_agent
[`https.request()`]: #https_https_request_options_callback
[`tls.connect()`]: tls.html#tls_tls_connect_options_callback
[`tls.createSecureContext()`]: tls.html#tls_tls_createsecurecontext_options
[`tls.createServer()`]: tls.html#tls_tls_createserver_options_secureconnectionlistener
[`url.parse()`]: url.html#url_url_parse_urlstring_parsequerystring_slashesdenotehost
