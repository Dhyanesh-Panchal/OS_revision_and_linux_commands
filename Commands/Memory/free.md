# `free` Command Documentation

The `free` command displays the amount of memory currently used (Physical & Swapped) in the system.

## Basic Usage
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

### total = used + free + buff/cache
### available (approx) = free + (reclaimable) buff/cache

## Output Fields Explained
- **free**: Memory that is completely unallocated
- **shared**: Memory that is used by multiple processes (shared libraries, shared memory segments)
- **buf/cache**: 
  - Buffer: Memory used by kernel buffers & Used as temporary storage of data before writing to disk
  - Cache: The page cache
- **available**: More accurate estimate of free RAM, as it accounts for buffer as well: *free + reclaimable(cache/buffer)*

## Useful Options
- `free -h`: Shows output in human-readable format (GB, MB, etc.)
- `free -s 3`: Updates output every 3 seconds