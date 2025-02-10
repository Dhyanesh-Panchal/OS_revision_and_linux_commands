# `strace` Systemcall trace.
- This is used to trace the systemcalls and signals a process makes during its execution.

### Syntax:
```sh
strace [options] command [command_args] # to test particular command


strace [options] -p <PID> # to trace already running process
```

| Option               | Description                                                                 |
|----------------------|-----------------------------------------------------------------------------|
| `-p <PID>`           | Attach to an already running process with given PID.                        |
| `-e trace=<syscall>` | Trace only specific system calls (e.g., `open`, `read`, `write`).           |
| `-e trace=file`      | Trace only file-related system calls.                                       |
| `-e trace=network`   | Trace network-related system calls.                                         |
| `-e trace=memory`    | Trace memory-related system calls.                                          |
| `-e trace=process`   | Trace process-related system calls (e.g., `fork`, `execve`).                |
| `-c`                 | Summary of system calls and their usage statistics.                         |
| `-o <file>`          | Save output to a file instead of printing to stdout.                        |
| `-s <num>`           | Limit the length of printed strings (default: 32).                          |
| `-f`                 | Trace child processes created via `fork()`.                                 |
| `-ff`                | Trace child processes separately with unique output files.                  |
| `-tt`                | Print timestamps with each system call.                                     |
| `-T`                 | Show time taken by each system call.                                        |
| `-x`                 | Print all non-ASCII strings in hex format.                                  |
| `-yy`                | Print file descriptor paths in full detail.                                 |

Example:
Trace all the systemcalls for any program:
`` strace ./script.sh``
Tracing the chrome for memory related systemcalls.
``strace -e type=memory -p <PID_of_chrome>``
