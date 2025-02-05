# `lsblk` List Block Devices

- The `lsblk` (list block devices) command is used to list information about all available block devices (e.g., hard drives, SSDs, USB drives) in a system. It displays the device names, sizes, types, mount points, and other attributes of block devices.

```sh
dhyanesh@dhyanesh-ThinkPad-T14s-Gen-1:~$ lsblk
NAME        MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
loop0         7:0    0     4K  1 loop /snap/bare/5
loop1         7:1    0  63.7M  1 loop /snap/core20/2434
loop2         7:2    0  73.9M  1 loop /snap/core22/1722
loop3         7:3    0  44.4M  1 loop /snap/snapd/23545
loop4         7:4    0  55.4M  1 loop /snap/core18/2846
loop5         7:5    0  63.3M  1 loop /snap/core20/1828
loop6         7:6    0  91.7M  1 loop /snap/gtk-common-themes/1535
loop7         7:7    0 970.5M  1 loop /snap/intellij-idea-community/562
loop8         7:8    0  64.5M  1 loop /snap/sublime-text/196
loop9         7:9    0 101.1M  1 loop /snap/teams-for-linux/741
loop10        7:10   0 349.7M  1 loop /snap/gnome-3-38-2004/143
loop11        7:11   0   1.1G  1 loop /snap/goland/335
loop12        7:12   0   1.1G  1 loop /snap/goland/331
loop13        7:13   0  73.9M  1 loop /snap/core22/1748
loop14        7:14   0 101.1M  1 loop /snap/teams-for-linux/730
loop15        7:15   0     1G  1 loop /snap/intellij-idea-community/566
loop16        7:16   0 346.3M  1 loop /snap/gnome-3-38-2004/119
loop17        7:17   0  49.9M  1 loop /snap/snapd/18357
loop18        7:18   0  64.5M  1 loop /snap/sublime-text/187
loop19        7:19   0 164.8M  1 loop /snap/gnome-3-28-1804/198
loop20        7:20   0    46M  1 loop /snap/snap-store/638
nvme0n1     259:0    0 238.5G  0 disk 
├─nvme0n1p1 259:1    0   512M  0 part /boot/efi
└─nvme0n1p2 259:2    0   238G  0 part /
```
- we can customize the output using `-o` flag Eg. `lsblk -o NAME,SIZE,TYPE,MOUNTPOINT`

### Field Descriptions
- **NAME**: The name of the device or partition (e.g., `sda`, `sda1`, `sdb`). It represents the device identifier used by the system.
- **MAJ:MIN**: The major and minor device numbers, used to identify the device in the kernel. **Each major number corresponds to a specific driver, which can handle multiple devices distinguished by minor numbers.** 
- **RM**: A flag indicating whether the device is removable. `1` for removable devices (e.g., USB drives), `0` for non-removable devices (e.g., internal HDD).
- **SIZE**: The size of the device or partition. For partitions, this is the size of the partition; for disks, it's the size of the entire disk.
- **RO**: Indicates if the device is read-only. `1` means the device is read-only (cannot write to it), `0` means it is writable.
- **TYPE**: The type of the device or partition:
  - `disk`: A physical disk (e.g., `sda`, `sdb`).
  - `part`: A partition (e.g., `sda1`, `sda2`).
  - `raid`: A RAID device.
  - `lvm`: A logical volume (from LVM).
  - `loop`: A loop device.
  - `crypt`: A device with encryption enabled (e.g., LUKS).
  - `rom`: A read-only memory device (e.g., CD-ROM).
- **MOUNTPOINT**: The mount point of the device or partition (e.g., `/`, `/mnt/data`). If not mounted, it will be blank.
- **UUID**: The Universally Unique Identifier for the device or partition, used for mounting and uniquely identifying storage devices.
- **FSTYPE**: The filesystem type (e.g., `ext4`, `xfs`, `btrfs`, `swap`) of the device or partition.
- **LABEL**: The label of the filesystem, if applicable (e.g., `MyDisk`, `Backup`). Labels are often used to identify volumes in a user-friendly manner.
- **PARTLABEL**: The partition label used to identify the partition (if a label exists).
- **PARTUUID**: The UUID of the partition itself, useful for identifying and mounting partitions without using device names like `/dev/sda1`.
- **MOUNTPOINT**: The location in the filesystem where the device or partition is mounted (e.g., `/mnt`, `/home`, `/var`).
