# `vmstat` Command Documentation

The `vmstat` command provides detailed information about system performance, including CPU usage, memory, swap activity, I/O statistics, and system processes.

## Basic Usage
```sh
dhyanesh@dhyanesh-ThinkPad-T14s-Gen-1:~/Desktop$ vmstat 2 4
procs -----------memory---------- ---swap-- -----io---- -system-- ------cpu-----
r  b   swpd   free   buff  cache   si   so    bi    bo   in   cs us sy id wa st
0  0      0 4229068 396520 5392644    0    0    13    79   95   41  4  1 95  0  0
0  0      0 4227304 396548 5392108    0    0     0   220 1482 3240  1  1 98  0  0
0  0      0 4206072 396556 5392088    0    0     0  1302 1493 3239  1  1 98  0  0
0  0      0 4227236 396556 5392156    0    0     0     0 1378 3113  1  1 98  0  0
```

## Output Fields Explained

### Processes (procs)
- **r**: Number of processes waiting for CPU time (Ready state). High values indicate CPU bottlenecks
- **b**: Number of processes in uninterruptible sleep (e.g., waiting for I/O)

### Memory
- **swpd**: Amount of swap memory in use (KB)
- **free**: Amount of completely free memory
- **buff**: Buffer memory (Memory used for temporary data before writing to disc)
- **cache**: Cache memory (Memory used for frequently accessed files)

### Swap Activity
- **si**: Swap in (KB/s) - Data moved from swap to RAM
- **so**: Swap out (KB/s) - Data moved from RAM to swap

### I/O
- **bi**: Blocks in (KB/s) - Disk data read from a block device
- **bo**: Blocks out (KB/s) - Disk data write to a block device

### System
- **in**: Interrupts per second (Hardware and software)
- **cs**: Number of process context switches per second

### CPU Usage (%)
- **us**: User CPU time - Time spent running user processes
- **sy**: System CPU time - Time spent on system processes
- **id**: Idle CPU time
- **wa**: I/O wait time
- **st**: Steal time - CPU time stolen by the hypervisor in a virtualized environment

## Additional Options
- `vmstat -d`: Displays stats about disk I/O for each block
- Alternatives: `dstat`, `iostat`, `netstat`
- Example: `dstat -tcmn` shows timestamped, CPU, memory, and network data