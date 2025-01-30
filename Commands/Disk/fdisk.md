# `fdisk`
- Fdisk is a command-line utility for disk partitioning. 
#### `sudo fdisk [options] <disk_device>`


- `sudo fdisk -l` can be used to list details of each partition.

### Commands description under fdisk.
| Command | Description | Usage Notes |
|---------|-------------|-------------|
| `m` | Print the help menu | - Lists all available commands<br>- Good starting point for new users |
| `p` | Print the current partition table | - Shows existing partitions<br>- Displays sizes, types, and partition numbers |
| `n` | Create a new partition | - Can create primary, extended, or logical partitions<br>- Will prompt for partition size<br>- Will ask for first and last sector |
| `d` | Delete a partition | - Requires partition number<br>- Cannot be undone until writing changes<br>- Use with caution |
| `t` | Change partition type | - Requires partition number<br>- Common types:<br>  - 83: Linux<br>  - 82: Linux swap<br>  - 8e: Linux LVM<br>  - 07: NTFS/exFAT |
| `w` | Write changes to disk | - **WARNING**: This is irreversible!<br>- Commits all changes to disk<br>- Verify changes with `p` before using |
| `q` | Quit without saving | - Exits fdisk without writing changes<br>- Safe option if mistakes were made |
| `g` | Create new GPT partition table | - **WARNING**: Destroys all existing data<br>- Used for disks larger than 2TB<br>- Required for UEFI systems |
| `o` | Create new MBR partition table | - **WARNING**: Destroys all existing data<br>- Traditional partition table type<br>- Limited to 2TB disk size |
| `v` | Verify partition table | - Checks for errors and inconsistencies<br>- Good practice before writing changes |
| `u` | Toggle units display | - Switches between sectors and cylinders<br>- Sectors recommended for precise sizing |

<!-- ## Common Workflow:
1. Start fdisk: `fdisk /dev/sdX`
2. Print current table: `p`
3. Make changes (create/delete partitions)
4. Verify changes: `p`
5. Write changes: `w` -->

### Loop Devices:
- A loop device in Linux is a pseudo-device that maps a file as a block device.
- It allows a file to be accessed as if it were a physical disk, making it useful for mounting disk images (like ISO files).
- Normally, block devices correspond to actual storage hardware (e.g., `/dev/sda`). However, a loop device (e.g., `/dev/loop0`, `/dev/loop1`) creates a virtual block device backed by a regular file.
- The kernel module `loop` manages these devices, and they can be *created manually using the `losetup` command*.