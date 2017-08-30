
* `setBreakpoint()`, `sb()` - Set breakpoint on current line
* `setBreakpoint(line)`, `sb(line)` - Set breakpoint on specific line
* `setBreakpoint('fn()')`, `sb(...)` - Set breakpoint on a first statement in
functions body
* `setBreakpoint('script.js', 1)`, `sb(...)` - Set breakpoint on first line of
script.js
* `clearBreakpoint('script.js', 1)`, `cb(...)` - Clear breakpoint in script.js
on line 1

It is also possible to set a breakpoint in a file (module) that
is not loaded yet:

```txt
$ node inspect test/fixtures/break-in-module/main.js
< Debugger listening on ws://127.0.0.1:9229/4e3db158-9791-4274-8909-914f7facf3bd
< For help see https://nodejs.org/en/docs/inspector
< Debugger attached.
Break on start in test/fixtures/break-in-module/main.js:1
> 1 (function (exports, require, module, __filename, __dirname) { const mod = require('./mod.js');
  2 mod.hello();
  3 mod.hello();
debug> setBreakpoint('mod.js', 22)
Warning: script 'mod.js' was not loaded yet.
debug> c
break in test/fixtures/break-in-module/mod.js:22
 20 // USE OR OTHER DEALINGS IN THE SOFTWARE.
 21
>22 exports.hello = function() {
 23   return 'hello from module';
 24 };
debug>
```

