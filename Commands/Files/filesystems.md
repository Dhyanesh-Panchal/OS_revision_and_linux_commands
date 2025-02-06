# filesystems in linux
- A filesystem is a method of storing, managing and accessing files on storage devices like hard drives, SSDs, etc.

| File System | Journaling | Max File Size | Max Volume Size | Special Features                     |
|-------------|------------|---------------|-----------------|--------------------------------------|
| Ext2        | No         | 16 TB         | 32 TB           | Older, no journaling                 |
| Ext3        | Yes        | 2 TB          | 32 TB           | Journaling support                   |
| Ext4        | Yes        | 16 TB         | 1 EB            | Faster, supports large files         |
| XFS         | Yes        | 8 EB          | 8 EB            | High-performance, scalable           |
| Btrfs       | Yes        | 16 EB         | 16 EB           | Snapshots, checksums, RAID           |

(*journaling is a feature which save changes to a filesystem in log called journal.*)

## Blocks
- A block is the smallest unit of data storage in a file system. When a file is stored, it is broken into blocks, and these blocks are distributed across the storage device.
- A block typically consists of **sectors** (smallest addressable unit of a disk, usually 512 bytes or 4 KB). The file system manages blocks to store and retrieve data efficiently.

## `ext4` Extended File System-4:
- Ext4 is the default file system for most Linux distributions.
- **Block size range from 1KB-64KB, (4KB default)**.
- There is NO builtin checksums.
### Ext4 File System Limits
| Feature               | Ext4                      |
|-----------------------|---------------------------|
| Max File Size         | 16 TB                     |
| Max Partition Size    | 1 EB (Exabyte)            |
| Max File Name Length  | 255 characters            |
| Max Number of Files   | ~4 billion (2^32)         |


## `brtfs` B-Tree File System:
- Btrfs is a **copy on write (COW)** filesystem for Linux aimed at implementing advanced features while focusing on fault tolerance, repair and easy administration.
- (COW) refers to a data management technique where any modification to a file results in creating a new copy of the data block instead of overwriting the original.
- Btrfs uses a dynamic block size system with fixed-size chunks to allocate storage.
