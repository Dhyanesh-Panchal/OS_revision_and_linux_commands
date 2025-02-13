# Virtual Memory related commands
## Process Memory Map
- A process  memory map shows how the process's address space is structured.
- It is stored at `/proc/<PID>/maps` for each process.
Example: ``cat /proc/$$/maps`` '$$' represents the current shell's PID
```sh
dhyanesh@dhyanesh-ThinkPad-T14s-Gen-1:~/Desktop/test_links$ cat /proc/$$/maps
address                 perms   offset    dev     inode                   pathname
5619981f1000-56199821e000 r--p 00000000 103:02 7995485                   /usr/bin/bash
56199821e000-5619982cf000 r-xp 0002d000 103:02 7995485                   /usr/bin/bash
5619982cf000-561998306000 r--p 000de000 103:02 7995485                   /usr/bin/bash
561998306000-56199830a000 r--p 00114000 103:02 7995485                   /usr/bin/bash
56199830a000-561998313000 rw-p 00118000 103:02 7995485                   /usr/bin/bash
561998313000-56199831d000 rw-p 00000000 00:00 0 
5619b1e6c000-5619b1fd0000 rw-p 00000000 00:00 0                          [heap]
7f8cce718000-7f8cce71b000 r--p 00000000 103:02 7997647                   /usr/lib/x86_64-linux-gnu/libnss_files-2.31.so
7f8cce71b000-7f8cce722000 r-xp 00003000 103:02 7997647                   /usr/lib/x86_64-linux-gnu/libnss_files-2.31.so
7f8cce722000-7f8cce724000 r--p 0000a000 103:02 7997647                   /usr/lib/x86_64-linux-gnu/libnss_files-2.31.so
7f8cce724000-7f8cce725000 r--p 0000b000 103:02 7997647                   /usr/lib/x86_64-linux-gnu/libnss_files-2.31.so
7f8cce725000-7f8cce726000 rw-p 0000c000 103:02 7997647                   /usr/lib/x86_64-linux-gnu/libnss_files-2.31.so
7f8cce726000-7f8cce72c000 rw-p 00000000 00:00 0 
7f8cce73d000-7f8ccecad000 r--p 00000000 103:02 7995509                   /usr/lib/locale/locale-archive
7f8ccecad000-7f8ccecb0000 rw-p 00000000 00:00 0 
...
```
### Column Break Down
- **Start-end Address**: Range of virtual memory segments.
- **Permissions**: `r`(read), `w`(write), `x`(execute), `p`(private), `s`(shared).
- **Offset**: If a region was mapped from a file (using `mmap`), this is the offset in the file where the maping begains.
- **device (MAJ:MIN)**: If the region was mapped from a file, this is the major and minor device number (in hex) where the file lives.
- **inode**: The filenumber of the file from which region was mapped.
- **pathname**: If the region was mapped from a file, this is the name of the file. There are also special regions with names like `[heap]`, `[stack]`, or `[vdso]`.


- Irix Mode is typically **enabled by default**.
