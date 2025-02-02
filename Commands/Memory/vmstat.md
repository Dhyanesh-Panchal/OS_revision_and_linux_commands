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

## Flags
- `vmstat -a` (Active/Inactive Memory) insted of (free-buff-cache)
- `vmstat -d` Reports disk I/O statistics (reads, writes, and totals).
    ```sh
    dhyanesh@dhyanesh-ThinkPad-T14s-Gen-1:~$ vmstat -d
    disk- ------------reads------------ ------------writes----------- -----IO------
        total merged sectors      ms  total merged sectors      ms    cur    sec
    loop0     14      0      34       0      0      0       0       0      0      0
    loop1    394      0   12466      40      0      0       0       0      0      0
    loop2     56      0    2146      16      0      0       0       0      0      0
    loop3    624      0   45814      82      0      0       0       0      0      1
    loop4     50      0     730      10      0      0       0       0      0      0
    loop5     45      0     698       5      0      0       0       0      0      0
    loop6   1790      0   10830      35      0      0       0       0      0      0
    loop7     57      0    2114       9      0      0       0       0      0      0
    nvme0n1  55300  14203 4665752   11069  77708 264273 9853394   73801      0     62
    loop12     54      0    2164      15      0      0       0       0      0      0
    loop11     61      0    2208      13      0      0       0       0      0      0
    loop15     61      0    2218      11      0      0       0       0      0      0
    loop8     58      0    2192      14      0      0       0       0      0      0
    loop14     55      0    2146       9      0      0       0       0      0      0
    loop13    364      0   11102      41      0      0       0       0      0      0
    loop16     54      0    2146      13      0      0       0       0      0      0
    loop10   1440      0   28038      56      0      0       0       0      0      0
    loop17     43      0     696       7      0      0       0       0      0      0
    loop18     52      0    2164      14      0      0       0       0      0      0
    loop9   3307      0  328106     405      0      0       0       0      0     12
    loop19    820      0   32414      83      0      0       0       0      0      1
    loop20    987      0   22350      57      0      0       0       0      0      1
    loop21     11      0      28       0      0      0       0       0      0      0
    ```
    - **disk**: Name of the disk or partition (e.g., `sda`, `sdb1`).
    - **total**: Total number of reads completed successfully.
    - **merged**: Number of merged reads (grouped for efficiency).
    - **sectors**: Total number of sectors read (1 sector = 512 bytes).
    - **ms**: Total time (in milliseconds) spent reading.
    - **total**: Total number of writes completed successfully.
    - **merged**: Number of merged writes (grouped for efficiency).
    - **sectors**: Total number of sectors written (1 sector = 512 bytes).
    - **ms**: Total time (in milliseconds) spent writing.
    - **cur**: Number of I/O operations currently in progress.
    - **sec**: Total time (in seconds) spent on I/O operations.
    - High sectors/ms: Indicates heavy disk I/O.
    - High cur: Shows active I/O operations (potential bottleneck).
    - merged: Reflects efficiency in grouping I/O requests.



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


## Value thresholds

| **Column**   | **Meaning** | **Usual Insight Range** | **Scenarios and Insights** |
|-------------|------------|-----------------|----------------------|
| **procs (r)** | Number of processes waiting for CPU | Normally `0-2` in idle systems; high values (`>4`) indicate CPU contention. | If `r` is consistently high, CPU is overloaded, and processes are waiting for execution. |
| **procs (b)** | Number of processes blocked (waiting for I/O) | Normally `0`. If `>1`, there may be a disk bottleneck. | High `b` value suggests slow disk I/O or a failing disk. Check with `iostat` or `iotop`. |
| **swpd** | Swap memory used (KB) | Ideally `0`. If `>0`, swapping is occurring, affecting performance. | High `swpd` suggests memory pressure. Check RAM usage and reduce unnecessary applications. |
| **free** | Free RAM (KB) | Varies; modern systems keep low free memory since Linux uses RAM for caching. | A sudden drop in `free` memory could indicate a memory leak or a heavy application consuming RAM. |
| **buff** | Memory used for buffers (KB) | Typically in tens to hundreds of MBs. | Buffers are used for disk operations. A steady decrease might indicate high disk read/write operations. |
| **cache** | Memory used for caching files (KB) | Normally large; Linux aggressively caches files to speed up access. | If cache suddenly drops, it may indicate high memory demand from running applications. |
| **si (swap in)** | Swap memory read from disk (KB/s) | Normally `0`. If `>0`, system is swapping in data from disk. | Frequent `si` values mean the system is out of RAM, leading to performance degradation. |
| **so (swap out)** | Swap memory written to disk (KB/s) | Ideally `0`. If `>0`, system is actively swapping data out. | High `so` values suggest heavy memory pressure. Consider adding more RAM. |
| **bi (block in)** | Blocks received from a block device (KB/s) | Normally low; spikes indicate disk read activity. | High `bi` suggests disk-intensive tasks like database queries, backups, or file reads. |
| **bo (block out)** | Blocks sent to a block device (KB/s) | Normally low; spikes indicate disk write activity. | High `bo` suggests disk writes due to logging, file saves, or large writes. |
| **in** | Interrupts per second | Varies, but typically in the range of `100-1000`. | Very high values (`>2000`) could indicate excessive hardware interrupts from devices like network cards. |
| **cs** | Context switches per second | Normally `1000-5000` but varies by workload. | Very high `cs` (`>10000`) means excessive task switching, often due to too many small tasks running simultaneously. |
| **us (user CPU)** | CPU time spent on user processes (%) | `5-50%` under normal loads. | If `us` is consistently high (`>80%`), an application is consuming CPU. Check with `top` or `htop`. |
| **sy (system CPU)** | CPU time spent on system (kernel) processes (%) | Normally `1-20%`. | High `sy` (`>30%`) suggests kernel-intensive tasks like heavy disk or network activity. |
| **id (idle CPU)** | Percentage of CPU idle time | Ideally `>70%` in an idle system. | If `id` is low (`<20%`), the system is busy. Investigate high CPU usage processes. |
| **wa (IO wait CPU)** | CPU waiting for I/O operations to complete (%) | Normally `0-5%`. If `>10%`, there is an I/O bottleneck. | High `wa` suggests slow disk or network storage issues. Check disk health and performance. |
| **st (steal CPU)** | CPU cycles "stolen" by the hypervisor (only in VMs) (%) | Ideally `0%`. If `>10%`, VM host is overloaded. | High `st` means other VMs are consuming too much CPU. Consider upgrading resources. |
 