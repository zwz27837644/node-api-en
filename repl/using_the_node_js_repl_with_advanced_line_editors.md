
For advanced line-editors, start Node.js with the environmental variable
`NODE_NO_READLINE=1`. This will start the main and debugger REPL in canonical
terminal settings, which will allow use with `rlwrap`.

For example, the following can be added to a `.bashrc` file:

```text
alias node="env NODE_NO_READLINE=1 rlwrap node"
```

