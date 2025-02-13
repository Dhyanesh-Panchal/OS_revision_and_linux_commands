# Process Control commands

## `kill [signal] PID`
- The `kill` command is used to send signals to processes, typically to terminate them. It works by sending a specific signal to a process ID (PID).
- If no signal is specified, `kill` sends **SIGTERM (15)** by default.

| Signal   | Number | Description                                      |
|----------|--------|--------------------------------------------------|
| `SIGHUP`   | 1      | Hang up, often used to reload configurations     |
| `SIGINT`   | 2      | Interrupt (like Ctrl+C)                          |
| `SIGKILL`  | 9      | Immediately kill the process (cannot be ignored) |
| `SIGTERM`  | 15     | Gracefully terminate (default)                   |
| `SIGSTOP`  | 19     | Pause the process (like Ctrl+Z)                  |
| `SIGCONT`  | 18     | Continue a stopped process                       |

- There are **total 64 types of such Interrupts**.
- use `kill -l` to list all the interrupts.

## `killall [options] process_name`
- The `killall` command is similar to `kill`, but instead of specifying a process ID (PID), you provide the process name. It is useful when you want to terminate all instances of a particular program.


## `nice -n [priority] command`
- The `nice` command is used to start a process with a defined priority (niceness value).
- Eg. ``sudo nice -n -5 python script.py`` will start script.py with priority -5.
- nice values range from *-20 to 19*. Lower the nice, higher the priority.
- *Assigning -ve priority requires root privileges*.

## `renice`
    ```sh
    renice -n [priority] -p PID
    renice -n [priority] -u user
    ```
- `renice` changes the priority of already running process.

## `jobs`
- A **process** is an instance of a running program managed by the kernel while, **job** is a shell-specific concept referring to one or more processes grouped together and managed by the shell's job control mechanism (e.g., foreground/background execution, suspending, resuming).
- If you add an ampersand (`&`) at the end, like `sleep 60 &`, it becomes a background job.
- It lists all background and suspended jobs in the current shell.

## `bg [job_id]`
- The `bg` command resumes a stopped job in the background.
## `fg [job_id]`
- The `fg` command brings a background job to the foreground.

```sh
dhyanesh@dhyanesh-ThinkPad-T14s-Gen-1:~$ traceroute google.com
traceroute to google.com (142.250.192.14), 30 hops max, 60 byte packets
 1  _gateway (10.20.40.1)  1.587 ms  1.503 ms  1.686 ms
^Z
[2]+  Stopped                 traceroute google.com
dhyanesh@dhyanesh-ThinkPad-T14s-Gen-1:~$ jobs
[1]-  Running                 sleep 1000 &
[2]+  Stopped                 traceroute google.com
dhyanesh@dhyanesh-ThinkPad-T14s-Gen-1:~$ fg %2
traceroute google.com
 2  27.109.19.37 (27.109.19.37)  3.695 ms  3.661 ms  3.629 ms
 3  202.131.123.233 (202.131.123.233)  3.599 ms  3.570 ms  3.541 ms
 4  27.109.9.113 (27.109.9.113)  4.857 ms  4.828 ms  4.797 ms
^Z
[2]+  Stopped                 traceroute google.com
dhyanesh@dhyanesh-ThinkPad-T14s-Gen-1:~$ jobs
[1]-  Running                 sleep 1000 &
[2]+  Stopped                 traceroute google.com
dhyanesh@dhyanesh-ThinkPad-T14s-Gen-1:~$ bg %2
[2]+ traceroute google.com &
dhyanesh@dhyanesh-ThinkPad-T14s-Gen-1:~$  5  120.72.93.121 (120.72.93.121)  8.396 ms  8.367 ms  8.338 ms
 6  202.131.106.45 (202.131.106.45)  5.022 ms  8.355 ms  8.276 ms
 7  202.131.98.145 (202.131.98.145)  5.727 ms  5.950 ms  5.902 ms
 8  202.131.99.94 (202.131.99.94)  13.445 ms  13.407 ms  13.370 ms
 9  27.109.1.197 (27.109.1.197)  13.322 ms  13.285 ms  13.249 ms
10  202.131.99.201 (202.131.99.201)  13.224 ms  13.190 ms  13.153 ms
11  * * *
12  142.251.64.14 (142.251.64.14)  13.725 ms 142.250.235.10 (142.250.235.10)  13.259 ms 108.170.238.198 (108.170.238.198)  11.817 ms
13  142.250.226.66 (142.250.226.66)  12.821 ms 192.178.111.60 (192.178.111.60)  14.584 ms bom12s14-in-f14.1e100.net (142.250.192.14)  12.757 ms

[2]+  Done                    traceroute google.com
``` 


## `chrt` Can be used to change the process scheduling policy.