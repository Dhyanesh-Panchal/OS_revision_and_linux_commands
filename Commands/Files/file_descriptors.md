# File Descriptors

File descriptors are integer values that refer to an open file in a process. They are used to read from or write to files, sockets, and other I/O resources.

| **File Descriptor** | **Description**                                 | **Default Behavior**                      | **Common Uses** |
|---------------------|-------------------------------------------------|------------------------------------------|-----------------|
| `0`                 | Standard Input (stdin)                         | Reads input from the terminal or file    | Input to programs |
| `1`                 | Standard Output (stdout)                       | Writes output to the terminal or file    | Output from programs |
| `2`                 | Standard Error (stderr)                        | Writes error messages to the terminal    | Error output in programs |
| `3+`                | User-defined file descriptors                   | Assigned dynamically for new open files | File operations (e.g., reading, writing) |

### File Descriptor Usage:
- **stdin (0)**: Typically used for input from keyboard or redirected input files.
- **stdout (1)**: Used for regular output, which can be redirected to a file or pipe.
- **stderr (2)**: Used specifically for error messages, typically not redirected by default.
- **3 and beyond**: These are used for any other files opened by the program, such as files, sockets, or pipes.

File descriptors are associated with a specific file or resource after the `open()` system call, and they allow a program to interact with various I/O resources.

### File Descriptor Operations:
- `close(fd)` – Closes the file descriptor `fd`.
- `read(fd, buf, count)` – Reads from the file descriptor into `buf`.
- `write(fd, buf, count)` – Writes to the file descriptor from `buf`.
- `dup(fd)` – Duplicates the file descriptor `fd` to the lowest available file descriptor.
- `dup2(oldfd, newfd)` – Duplicates `oldfd` to `newfd`.

### File Descriptor Limits:
- Typically, each process has a limit on the number of open file descriptors, which can be viewed and adjusted using `ulimit -n`.
