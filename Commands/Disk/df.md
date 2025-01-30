# `df` (Disk Free)
- The `df` command displays information about file system disk space usage on the mounted file system. This command retrieves the information from `/proc/mounts` or `/etc/mtab`.
- `df` command shows disk space in Kilobytes (KB) by default.
```sh
dhyanesh@dhyanesh-ThinkPad-T14s-Gen-1:~$ df
Filesystem     1K-blocks     Used Available Use% Mounted on
udev             7948520        0   7948520   0% /dev
tmpfs            1599132     2164   1596968   1% /run
/dev/nvme0n1p2 244506940 29081448 202932436  13% /
tmpfs            7995660   404432   7591228   6% /dev/shm
tmpfs               5120        4      5116   1% /run/lock
tmpfs            7995660        0   7995660   0% /sys/fs/cgroup
/dev/loop0           128      128         0 100% /snap/bare/5
/dev/loop1         65280    65280         0 100% /snap/core20/2434
/dev/loop2         75648    75648         0 100% /snap/core22/1722
/dev/loop4         56704    56704         0 100% /snap/core18/2846
/dev/loop3         45568    45568         0 100% /snap/snapd/23545
/dev/loop5         64896    64896         0 100% /snap/core20/1828
/dev/loop8         66048    66048         0 100% /snap/sublime-text/196
/dev/loop16       354688   354688         0 100% /snap/gnome-3-38-2004/119
/dev/loop6         93952    93952         0 100% /snap/gtk-common-themes/1535
/dev/loop11      1160960  1160960         0 100% /snap/goland/335
/dev/loop13        75776    75776         0 100% /snap/core22/1748
/dev/loop12      1160960  1160960         0 100% /snap/goland/331
/dev/loop14       103552   103552         0 100% /snap/teams-for-linux/730
/dev/loop15      1049600  1049600         0 100% /snap/intellij-idea-community/566
/dev/loop17        51072    51072         0 100% /snap/snapd/18357
/dev/loop7        993792   993792         0 100% /snap/intellij-idea-community/562
/dev/loop10       358144   358144         0 100% /snap/gnome-3-38-2004/143
/dev/loop18        66048    66048         0 100% /snap/sublime-text/187
/dev/loop9        103680   103680         0 100% /snap/teams-for-linux/741
/dev/loop19       168832   168832         0 100% /snap/gnome-3-28-1804/198
/dev/loop20        47104    47104         0 100% /snap/snap-store/638
/dev/nvme0n1p1    523248     6220    517028   2% /boot/efi
tmpfs            1599132       40   1599092   1% /run/user/1000
```
## Formating Option:
```sh
df -h    # Human-readable format (e.g., 1K, 234M, 2G)
df -H    # SI units (powers of 1000 instead of 1024)
df -T    # Include filesystem type
df -i    # Show inode information instead of block usage
```

```sh
dhyanesh@dhyanesh-ThinkPad-T14s-Gen-1:~$ df -hT
Filesystem     Type      Size  Used Avail Use% Mounted on
udev           devtmpfs  7.6G     0  7.6G   0% /dev
tmpfs          tmpfs     1.6G  2.2M  1.6G   1% /run
/dev/nvme0n1p2 ext4      234G   28G  194G  13% /
tmpfs          tmpfs     7.7G  374M  7.3G   5% /dev/shm
tmpfs          tmpfs     5.0M  4.0K  5.0M   1% /run/lock
tmpfs          tmpfs     7.7G     0  7.7G   0% /sys/fs/cgroup
/dev/loop0     squashfs  128K  128K     0 100% /snap/bare/5
/dev/loop1     squashfs   64M   64M     0 100% /snap/core20/2434
/dev/loop2     squashfs   74M   74M     0 100% /snap/core22/1722
/dev/loop4     squashfs   56M   56M     0 100% /snap/core18/2846
/dev/loop3     squashfs   45M   45M     0 100% /snap/snapd/23545
/dev/loop5     squashfs   64M   64M     0 100% /snap/core20/1828
.
.
.
```
### Fields in output:
- **Filesystem**: The device/partition name
- **Type**: The filesystem type (ext4, xfs, tmpfs, etc.)
- **Size**: Total size of the filesystem
- **Used**: Amount of space used
- **Avail**: Amount of space available
- **Use%**: Percentage of space used
- **Mounted** on: The mount point in the filesystem hierarchy

```sh
dhyanesh@dhyanesh-ThinkPad-T14s-Gen-1:~$ df -hiT
Filesystem     Type     Inodes IUsed IFree IUse% Mounted on
udev           devtmpfs   1.9M   583  1.9M    1% /dev
tmpfs          tmpfs      2.0M  1.2K  2.0M    1% /run
/dev/nvme0n1p2 ext4        15M  312K   15M    3% /
tmpfs          tmpfs      2.0M  2.0K  2.0M    1% /dev/shm
tmpfs          tmpfs      2.0M     5  2.0M    1% /run/lock
tmpfs          tmpfs      2.0M    19  2.0M    1% /sys/fs/cgroup
/dev/loop0     squashfs     29    29     0  100% /snap/bare/5
/dev/loop1     squashfs    12K   12K     0  100% /snap/core20/2434
/dev/loop2     squashfs    14K   14K     0  100% /snap/core22/1722
/dev/loop4     squashfs    11K   11K     0  100% /snap/core18/2846
/dev/loop3     squashfs    608   608     0  100% /snap/snapd/23545
/dev/loop5     squashfs    12K   12K     0  100% /snap/core20/1828
/dev/loop8     squashfs    15K   15K     0  100% /snap/sublime-text/196
/dev/loop16    squashfs    18K   18K     0  100% /snap/gnome-3-38-2004/119
/dev/loop6     squashfs    75K   75K     0  100% /snap/gtk-common-themes/1535
/dev/loop11    squashfs   2.5K  2.5K     0  100% /snap/goland/335
/dev/loop13    squashfs    14K   14K     0  100% /snap/core22/1748
/dev/loop12    squashfs   2.5K  2.5K     0  100% /snap/goland/331
/dev/loop14    squashfs    137   137     0  100% /snap/teams-for-linux/730
/dev/loop15    squashfs   2.0K  2.0K     0  100% /snap/intellij-idea-community/566
/dev/loop17    squashfs    496   496     0  100% /snap/snapd/18357
/dev/loop7     squashfs   1.9K  1.9K     0  100% /snap/intellij-idea-community/562
/dev/loop10    squashfs    18K   18K     0  100% /snap/gnome-3-38-2004/143
/dev/loop18    squashfs    15K   15K     0  100% /snap/sublime-text/187
/dev/loop9     squashfs    137   137     0  100% /snap/teams-for-linux/741
/dev/loop19    squashfs    28K   28K     0  100% /snap/gnome-3-28-1804/198
/dev/loop20    squashfs    17K   17K     0  100% /snap/snap-store/638
/dev/nvme0n1p1 vfat          0     0     0     - /boot/efi
tmpfs          tmpfs      2.0M   101  2.0M    1% /run/user/1000
```
### Inode:
- An inode (index node) is a data structure used by the Linux filesystem to store metadata about a file.
- Every file in a Linux filesystem has an associated inode, which contains information about the file except for its name and content.
- List inode : `ls -i filename`

### Filesystem based options
```sh
df -a    # Show all filesystems, including virtual ones
df -l    # Show only local filesystems
df -P    # Use POSIX output format
df -x tmpfs    # Exclude specific filesystem types
```
- **Linux reserves 5% of filesystem space by default for root user**

- Select files of specific fileformat `df -hT | grep "ext4"`
