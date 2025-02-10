# System Calls

A system call is used to access privileged services from the kernel. It acts as an interface between a user process and the operating system (kernel). When a program needs to perform operations like file handling, process control, or memory management, it makes a system call, which is handled by the kernel.

## Steps Involved in a System Call

1. **System Call Invocation**:
    - When a user process makes a system call (e.g., `read()`), it triggers a software interrupt, switching the CPU from user mode to kernel mode.

2. **Interrupts During System Call**:
    - While in kernel mode, hardware interrupts (e.g., from I/O devices) or software interrupts (e.g., from other processes) can occur.
    - The kernel pauses the system call, handles the interrupt, and then resumes the system call.

3. **Handling Interrupts**:
    - The CPU saves the current process state, handles the interrupt, and then restores the process state to continue the system call.

4. **Return to User Mode**:
    - After the system call completes and any interrupts are handled, the CPU returns to user mode, allowing the process to continue execution.

## Types of System Calls

### 1. Process Control System Calls

1. **`fork()`**
    - Creates a new child process, identical to the parent process but with a different PID.
    - **Return Values of `fork()`**:
      - `0` : In the child process.
      - `> 0` : In the parent process (returns child process PID).
      - `< 0` : Error in creating a child process.

2. **`exec()`**
    - Stops the current process’s execution and starts executing a new process specified in the `exec()` call.
    - Generally used with `fork()` to create and associate child processes with respective tasks.
    - **Behavior of `exec()`**:
      - PID remains the same.
      - Memory, stack, and data segments are replaced by the new process.
      - Does not return unless there is an error.

3. **`exit()`**
    - Terminates the current process and returns an exit status.
    - **Exit Codes**:
      - `0` : Success.
      - Non-zero : Error.

### 2. File Operations System Calls

- **`open()`** : Opens a file.
- **`read()`** : Reads data from a file.
- **`write()`** : Writes data to a file.
- **`close()`** : Closes a file.

### 3. Inter-Process Communication (IPC) System Calls

- **`pipe()`** : Establishes unidirectional communication between processes.
- **`socket()`** : Creates an endpoint for communication.
- **`send()`** : Sends data over a socket.
- **`recv()`** : Receives data from a socket.

### 4. Device Management System Calls

- **`ioctl()`** : Performs device-specific input/output operations.
- **`read()`** : Reads data from a device.
- **`write()`** : Writes data to a device.



## `mmap()` Memory map & `munmap()` Memory Unmap.
- `mmap` is a systemcall that maps files and devices to the memory.
- `mmap()` creates a new mapping in the **virtual address space** of the calling process.
- It allows a process to directly access file data as if it were part of its address space, enabling efficient file I/O and shared memory between processes. 
#### Usage in Standard C Library:
```c
#include <sys/mman.h>

void *mmap(void addr[.length], size_t length, int prot, int flags, int fd, off_t offset);
```
- The starting address for the new mapping is specified in `addr`.
    - If `addr` is `NULL`, then the kernel chooses the *(page-aligned)*
       address at which to create the mapping; this is the most portable
       method of creating a new mapping.
    - *A page-aligned address is a memory address that is a multiple of the system's page size. Typically 4 KB (4096 bytes)*.
    - It is recomendede to use mmap with **`NULL` addr** and let kernel handle the address selection.
    - If `addr` is Not `NULL`, then the
       kernel takes it as a hint about where to place the mapping; on
       Linux, the kernel will pick a nearby page boundary *(but always above or equal to the value specified by `/proc/sys/vm/mmap_min_addr`)* and attempt to create the mapping there.
- The `length` specifies the length of the mapping.

- The address of the new mapping is returned as the result of the call.


- One of the option in mmap is `MAP_SHARED`, which makes the request memory mapping **shared accross the parent and subsequent child process**, i.e *if parent changes the information at particular location, it reflects accross all child processes, and vice versa.*
Reference: [here](https://www.youtube.com/watch?v=8hVLcyBkSXY)





