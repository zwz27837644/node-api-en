
<!--type=misc-->

On Linux and macOS systems, `fs.watch()` resolves the path to an [inode][] and
watches the inode. If the watched path is deleted and recreated, it is assigned
a new inode. The watch will emit an event for the delete but will continue
watching the *original* inode. Events for the new inode will not be emitted.
This is expected behavior.

In AIX, save and close of a file being watched causes two notifications -
one for adding new content, and one for truncation. Moreover, save and
close operations on some platforms cause inode changes that force watch
operations to become invalid and ineffective. AIX retains inode for the
lifetime of a file, that way though this is different from Linux / macOS,
this improves the usability of file watching. This is expected behavior.

