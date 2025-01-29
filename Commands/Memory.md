1. `free`: it displays the amount of memory currently used (Physical & Swapped).
    ```sh
    dhyanesh@dhyanesh-ThinkPad-T14s-Gen-1:~/Desktop$ free
                    total        used        free      shared  buff/cache   available
        Mem:       15991316     5965564     4265972     1373236     5759780     8015032
        Swap:       2097148           0     2097148
        dhyanesh@dhyanesh-ThinkPad-T14s-Gen-1:~/Desktop$ free -h
                    total        used        free      shared  buff/cache   available
        Mem:           15Gi       5.7Gi       4.1Gi       1.3Gi       5.5Gi       7.7Gi
        Swap:         2.0Gi          0B       2.0Gi
    ```

    - *free*: Memory that is completely unallocated.
    - *shared*: Memory that is used by multiple processes(shared libraries, shared memory segments).
    - *buf/cache*: (Buffer) Used as temporary storage of data before writing to disk. (cache) is the page cache.
    - *available*: This is more accurate estimate of free RAM, as it accounts for buffer aswell: *free + reclaimable(cache/buffer)*
    - ``free -s 3`` updates output every 3 second.
    ---
1. `vmstat [options] [delay] [count]`: provides detailed information about system performance, including CPU usage, memory, swap activity, I/O statistics, and system processes.
    - Eg. display every 2 sec, 4 times.
    ```sh
    dhyanesh@dhyanesh-ThinkPad-T14s-Gen-1:~/Desktop$ vmstat 2 4
    procs -----------memory---------- ---swap-- -----io---- -system-- ------cpu-----
    r  b   swpd   free   buff  cache   si   so    bi    bo   in   cs us sy id wa st
    0  0      0 4229068 396520 5392644    0    0    13    79   95   41  4  1 95  0  0
    0  0      0 4227304 396548 5392108    0    0     0   220 1482 3240  1  1 98  0  0
    0  0      0 4206072 396556 5392088    0    0     0  1302 1493 3239  1  1 98  0  0
    0  0      0 4227236 396556 5392156    0    0     0     0 1378 3113  1  1 98  0  0
    ```
    - *r*: (runnable) Number of processes waiting for CPU time. (in Ready state), *High values indicate CPU bottlenecks.*
    - *b*: (blocked) Number of processes in uninterruptible sleep (e.g., waiting for I/O).
    - *swpd*: Amount of swap memory in use. in KB
    - *free*: Amount of completely free memory.
    - *buff*: buffer memory. (Memory used for temporary data before writing to disc.)
    - *cache*: cache memory. (Memory used for frequently accessed files.) 
    - *si*: swap in(KB/s), Data moved from swap to RAM.
    - *so*: swap out(KB/s), Data moved from RAM to swap.
    - *bi*: blocks in(KB/s), Disk data read from a block device, (I/O) operation.
    - *bo*: block out(KB/s), Disk data write to a block device, (I/O).
    - *in*: Interrupts per sec (Hardware and software).
    - *cs*: no. of process context switches per sec.
    - *us*: (user CPU time, %), Percentage of CPU time spent running user processes.
    - *sy*: (sys CPU time, %), Percentage of CPU time spent on system processes.
    - *id*: (idle CPU time, %)
    - *wa*: (I/O wait, %)
    - *st* (steal time, %), CPU time stolen by the hypervisor in a virtualized environment.
    - `vmstat -d` displays stats about disk I/O for each block
    - `dstat`, `iostat`, `netstat` are alternatives to `vmstat`.
    - Eg. `dstat -tcmn` will show *timestamped, CPU, memory, network* data.
    ---
1. `dstat [options] [delay] [count]`: Better organized with more info.
    ```sh
    dhyanesh@dhyanesh-ThinkPad-T14s-Gen-1:~/Desktop$ dstat -t -c -m -d -g -n -r -p -l
    ----system---- --total-cpu-usage-- ------memory-usage----- -dsk/total- ---paging-- -net/total- --io/total- ---procs--- ---load-avg---
         time     |usr sys idl wai stl| used  free  buff  cach| read  writ|  in   out | recv  send| read  writ|run blk new| 1m   5m  15m 
    29-01 13:47:30|  4   1  95   0   0|7353M 3863M  423M 5083M|  54k  444k|   0     0 |   0     0 |1.38  8.03 |  0   0 0.2|0.52 0.48 0.55
    29-01 13:47:31|  1   1  98   0   0|7351M 3866M  423M 5092M|   0     0 |   0     0 |2214B  694B|   0     0 |2.0   0   0|0.52 0.48 0.55
    29-01 13:47:32|  2   1  97   0   0|7374M 3843M  423M 5091M|   0     0 |   0     0 |3323B    0 |   0     0 |  0   0   0|0.52 0.48 0.55
    29-01 13:47:33|  1   1  98   0   0|7367M 3850M  423M 5083M|   0     0 |   0     0 | 939B    0 |   0     0 |  0   0   0|0.47 0.47 0.55
    29-01 13:47:34|  2   2  96   0   0|7367M 3850M  423M 5084M|   0     0 |   0     0 | 606B   86B|   0     0 |1.0   0   0|0.47 0.47 0.55
    29-01 13:47:35|  4   1  95   0   0|7372M 3845M  423M 5084M|   0  7888k|   0     0 |1614B    0 |   0   358 |  0   0   0|0.47 0.47 0.55
    29-01 13:47:36|  1   1  97   0   0|7368M 3848M  423M 5084M|   0     0 |   0     0 | 959B  282B|   0     0 |  0   0   0|0.47 0.47 0.55
    29-01 13:47:37|  1   1  99   0   0|7359M 3857M  423M 5084M|   0     0 |   0     0 | 660B    0 |   0     0 |  0   0   0|0.47 0.47 0.55
    29-01 13:47:38|  2   1  97   0   0|7351M 3866M  423M 5083M|   0     0 |   0     0 |1410B  172B|   0     0 |  0   0   0|0.52 0.48 0.55
    29-01 13:47:39|  2   1  98   0   0|7370M 3847M  423M 5083M|   0     0 |   0     0 | 873B    0 |   0     0 |  0   0   0|0.52 0.48 0.55
    29-01 13:47:40|  2   0  98   0   0|7367M 3849M  423M 5083M|   0  5544k|   0     0 |1251B    0 |   0  34.0 |  0   0 1.0|0.52 0.48 0.55
    ```
    - there multiple flags for specific information. refer --help for more. (each column is in seq. of flag)
    - *dsk/total*-KB/s, *paging*-pages/sec, *net/total*-bytes/sec, *I/O*-KB/s.
    ---
1. `top` & `htop`: top and htop are used for monitoring system processes, resource usage, and performance in real-time.
    - for `top`:
    ![top](../Images/top.png)
    - Tasks Breakdown: Running (R), Sleeping (S), UnInterruptable Sleep (D), Suspened processes (T), Zombie (Z).  
    - Breakdown of CPU usage as a percentage of time spent in user mode (us), system mode (sy), nice mode (ni), idle (id), waiting for I/O (wa), hardware interrupts (hi), software interrupts (si), and steal time (st).
    - *PID*: Process ID.
    - *USER*: User owning the process.
    - *PR*: Process priority. `(PR = 20 + NI)`
    - *NI*: Nice value (priority modifier).
    - *VIRT*: Virtual memory used by the process.
    - *RES*: Resident memory (physical memory) used by the process.
    - *SHR*: Shared memory used by the process.
    - *S*: Process state (e.g., running, sleeping).
    - *%CPU*: CPU usage of the process.
    - *%MEM*: Memory usage of the process.
    - *TIME*+: Total CPU time consumed by the process.
    - *COMMAND*: Command or name of the process.
    ---
    - `htop`: better version of top.
    ![htop](../Images/htop.png)
    - Other fields are similar to top.


