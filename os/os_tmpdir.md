<!-- YAML
added: v0.9.9
changes:
  - version: v2.0.0
    pr-url: https://github.com/nodejs/node/pull/747
    description: This function is now cross-platform consistent and no longer
                 returns a path with a trailing slash on any platform
-->

* Returns: {string}

The `os.tmpdir()` method returns a string specifying the operating system's
default directory for temporary files.

