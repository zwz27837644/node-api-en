
The following constants are meant for use with the [`fs.Stats`][] object's
`mode` property for determining the access permissions for a file.

<table>
  <tr>
    <th>Constant</th>
    <th>Description</th>
  </tr>
  <tr>
    <td><code>S_IRWXU</code></td>
    <td>File mode indicating readable, writable and executable by owner.</td>
  </tr>
  <tr>
    <td><code>S_IRUSR</code></td>
    <td>File mode indicating readable by owner.</td>
  </tr>
  <tr>
    <td><code>S_IWUSR</code></td>
    <td>File mode indicating writable by owner.</td>
  </tr>
  <tr>
    <td><code>S_IXUSR</code></td>
    <td>File mode indicating executable by owner.</td>
  </tr>
  <tr>
    <td><code>S_IRWXG</code></td>
    <td>File mode indicating readable, writable and executable by group.</td>
  </tr>
  <tr>
    <td><code>S_IRGRP</code></td>
    <td>File mode indicating readable by group.</td>
  </tr>
  <tr>
    <td><code>S_IWGRP</code></td>
    <td>File mode indicating writable by group.</td>
  </tr>
  <tr>
    <td><code>S_IXGRP</code></td>
    <td>File mode indicating executable by group.</td>
  </tr>
  <tr>
    <td><code>S_IRWXO</code></td>
    <td>File mode indicating readable, writable and executable by others.</td>
  </tr>
  <tr>
    <td><code>S_IROTH</code></td>
    <td>File mode indicating readable by others.</td>
  </tr>
  <tr>
    <td><code>S_IWOTH</code></td>
    <td>File mode indicating writable by others.</td>
  </tr>
  <tr>
    <td><code>S_IXOTH</code></td>
    <td>File mode indicating executable by others.</td>
  </tr>
</table>


[`AHAFS`]: https://www.ibm.com/developerworks/aix/library/au-aix_event_infrastructure/
[`Buffer.byteLength`]: buffer.html#buffer_class_method_buffer_bytelength_string_encoding
[`Buffer`]: buffer.html#buffer_buffer
[`FSEvents`]: https://developer.apple.com/library/mac/documentation/Darwin/Conceptual/FSEvents_ProgGuide/Introduction/Introduction.html#//apple_ref/doc/uid/TP40005289-CH1-SW1
[`ReadDirectoryChangesW`]: https://msdn.microsoft.com/en-us/library/windows/desktop/aa365465%28v=vs.85%29.aspx
[`ReadStream`]: #fs_class_fs_readstream
[`URL`]: url.html#url_the_whatwg_url_api
[`WriteStream`]: #fs_class_fs_writestream
[`event ports`]: http://illumos.org/man/port_create
[`fs.FSWatcher`]: #fs_class_fs_fswatcher
[`fs.Stats`]: #fs_class_fs_stats
[`fs.access()`]: #fs_fs_access_path_mode_callback
[`fs.appendFile()`]: fs.html#fs_fs_appendfile_file_data_options_callback
[`fs.exists()`]: fs.html#fs_fs_exists_path_callback
[`fs.fstat()`]: #fs_fs_fstat_fd_callback
[`fs.futimes()`]: #fs_fs_futimes_fd_atime_mtime_callback
[`fs.lstat()`]: #fs_fs_lstat_path_callback
[`fs.mkdtemp()`]: #fs_fs_mkdtemp_prefix_options_callback
[`fs.open()`]: #fs_fs_open_path_flags_mode_callback
[`fs.read()`]: #fs_fs_read_fd_buffer_offset_length_position_callback
[`fs.readFile()`]: #fs_fs_readfile_path_options_callback
[`fs.readFileSync()`]: #fs_fs_readfilesync_path_options
[`fs.stat()`]: #fs_fs_stat_path_callback
[`fs.utimes()`]: #fs_fs_utimes_path_atime_mtime_callback
[`fs.watch()`]: #fs_fs_watch_filename_options_listener
[`fs.write()`]: #fs_fs_write_fd_buffer_offset_length_position_callback
[`fs.writeFile()`]: #fs_fs_writefile_file_data_options_callback
[`inotify`]: http://man7.org/linux/man-pages/man7/inotify.7.html
[`kqueue`]: https://www.freebsd.org/cgi/man.cgi?kqueue
[`net.Socket`]: net.html#net_class_net_socket
[`stat()`]: fs.html#fs_fs_stat_path_callback
[`util.inspect(stats)`]: util.html#util_util_inspect_object_options
[`util.promisify()`]: util.html#util_util_promisify_original
[Caveats]: #fs_caveats
[Common System Errors]: errors.html#errors_common_system_errors
[FS Constants]: #fs_fs_constants_1
[MDN-Date]: https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Date
[MDN-Number]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Data_structures#Number_type
[MSDN-Rel-Path]: https://msdn.microsoft.com/en-us/library/windows/desktop/aa365247.aspx#fully_qualified_vs._relative_paths
[Readable Stream]: stream.html#stream_class_stream_readable
[Writable Stream]: stream.html#stream_class_stream_writable
[inode]: https://en.wikipedia.org/wiki/Inode
[Naming Files, Paths, and Namespaces]: https://msdn.microsoft.com/en-us/library/windows/desktop/aa365247(v=vs.85).aspx
[MSDN-Using-Streams]: https://msdn.microsoft.com/en-us/library/windows/desktop/bb540537.aspx
