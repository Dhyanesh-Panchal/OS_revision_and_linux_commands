# Kernels
- A kernel is the core component of an operating system (OS) that acts as a bridge between hardware and software. It manages system resources such as CPU, memory, and I/O devices, ensuring smooth operation of processes and services.

## Functions of kernel:
1. **Process Management**: Handles process creation, scheduling, and termination.
2. **Memory Management**: Allocates and De-allocates memory to the process.
3. **Device Management**: Interface with hardware using device drivers.
4. **File System Management**: Manages File read-write.
5. **System Calls and API**: Provides a mechanism for applications to communicate with hardware.

## Types of kernels:
### 1. Monolithic Kernel:
A monolithic kernel is a single large program where all essential OS services (e.g., process management, memory management, device drivers, file system) run in kernel space.
- Examples: Linux kernel, UNIX kernel, MS-DOS, etc.
- Linux kernel is not strictly monolithic, rather its Modular-Monolithic. Refer: [Linux kernel](./Linux_kernel.md)

### 2. Microkernel:
A microkernel only includes the most essential functions in kernel space (like inter-process communication and memory management), while other services (e.g., file system, device drivers) run in user space.
- Examples: Minix, QNX, L4, etc.

### 3. Hybrid Kernel:
A hybrid kernel is a combination of features of both monolithic and microkernel. It runs some critical services in kernel space for performance, but keeps others in userspace.

### 4. Exokernel:
An exokernel is a minimalistic kernel that gives applications direct access to hardware while keeping only security and resource multiplexing in the kernel.

### 5. Nanokernel:
A nanokernel is a even smaller kernel than microkernel. Its a type of kernel that provides only the most basic services a system needs to run. It's designed to be small, fast, and efficient, and is often used in systems with limited resources.

### 6. Modular kernel:
A modular kernel is a type of monolithic kernel that allows dynamically loading and unloading kernel modules at runtime.


### Comparison
| Kernel Type   | Performance       | Stability       | Ease of Development | Examples               |
|---------------|-------------------|-----------------|----------------------|------------------------|
| Monolithic    | ✅ High           | ❌ Lower        | ❌ Harder            | Linux, Unix            |
| Microkernel   | ❌ Lower          | ✅ Higher       | ✅ Easier            | Minix, QNX             |
| Hybrid        | ✅ Medium         | ✅ Medium       | ✅ Balanced          | Windows NT, macOS      |
| Exokernel     | ✅ Very High      | ❌ Lower        | ❌ Complex           | MIT Exokernel          |
| Nanokernel    | ❌ Lower          | ✅ Higher       | ✅ Easier            | Eros, K42              |