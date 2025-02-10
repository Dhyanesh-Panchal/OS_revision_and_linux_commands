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

