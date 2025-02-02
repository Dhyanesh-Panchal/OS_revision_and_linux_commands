# File Permissions and modification.

## File Permissions Reference

| **Symbolic Notation** | **Octal Value** | **Description**                                                                 |
|-----------------------|-----------------|---------------------------------------------------------------------------------|
| `----------`          | `0000`          | No permissions for anyone.                                                      |
| `-rwx------`          | `0700`          | Owner has **read, write, execute**.                                             |
| `-rw-r--r--`          | `0644`          | Owner: **read/write**; Group/Others: **read-only** (common for files).          |
| `-rwxr-xr-x`          | `0755`          | Owner: **read/write/execute**; Group/Others: **read/execute** (common for dirs).|
| `drwx------`          | `0700`          | **Directory** with owner having full access.                                    |
| `lrwxrwxrwx`          | `0777`          | **Symbolic link** (permissions are ignored, inherited from target).             |
| `-rwsr-xr-x`          | `4755`          | **Setuid**: Executes with owner's privileges.                                   |
| `-rwxr-sr-x`          | `2755`          | **Setgid**: Executes with group's privileges.                                   |
| `drwxrwxrwt`          | `1777`          | **Sticky bit**: Only owner can delete files in the directory (e.g., `/tmp`).    |

### Key Symbols:
- **First Character**: File type (`-` = file, `d` = directory, `l` = symlink, etc.).
- **Triplets**: Permissions for **User (Owner)**, **Group**, **Others** in order.
  - `r` = read (4), `w` = write (2), `x` = execute (1).
  - `s/S` = setuid/setgid, `t/T` = sticky bit.

### Common Commands:
- `ls -l`: View permissions in symbolic notation.
- `chmod <octal> <file>`: Set permissions numerically (e.g., `chmod 755 script.sh`).
- `chmod u+x <file>`: Add execute permission for the owner.

## Listing with permissions `ls -l`
```sh
dhyanesh@dhyanesh-ThinkPad-T14s-Gen-1:~/Desktop/test_go$ ls -l
total 8
-rw-rw-r-- 1 dhyanesh dhyanesh 102 Jan 31 10:36 cpu_intensive.go
-rw-rw-r-- 1 dhyanesh dhyanesh 117 Jan 30 14:01 test.go
```

## `chmod` for changing file permissions

Syntax: ``chmod <who><operator><permissions> <file/directory>``

| Flag | Description | Example |
|------|------------|---------|
| `+` | Adds the specified permission(s). | `chmod +x file.sh` (Add execute permission) |
| `-` | Removes the specified permission(s). | `chmod -x file.sh` (Remove execute permission) |
| `=` | Sets the specified permission(s) exactly, removing others. | `chmod u=r file.txt` (Set read-only for the user) |
| `u` | User (owner) permissions. | `chmod u+x file.sh` (Add execute permission to the owner) |
| `g` | Group permissions. | `chmod g-w file.txt` (Remove write permission from the group) |
| `o` | Others' permissions. | `chmod o=r file.txt` (Set read-only for others) |
| `a` | All users (user, group, others). | `chmod a+x file.sh` (Add execute permission for all users) |
| `r` | Read permission. | `chmod u+r file.txt` (Add read permission for the user) |
| `w` | Write permission. | `chmod g+w file.txt` (Add write permission for the group) |
| `x` | Execute permission. | `chmod o+x script.sh` (Add execute permission for others) |
| `777` | Full permissions (rwx for all). | `chmod 777 file.txt` (Read, write, execute for all) |
| `755` | Owner has full permissions, group & others have read/execute. | `chmod 755 script.sh` |
| `644` | Owner has read/write, others have read-only. | `chmod 644 document.txt` |
| `400` | Owner has read-only, no permissions for others. | `chmod 400 secret.txt` |

## `chown` for changing the file ownership and Group

Syntax: ``chown [options] <user>:<group> <file/directory>``

| Flag | Description | Example |
|------|------------|---------|
| `user:group` | Change owner and group. | `chown user1:group1 file.txt` |
| `user` | Change only the owner. | `chown user1 file.txt` |
| `:group` | Change only the group. | `chown :group1 file.txt` |
| `-R` | Recursively change ownership for all files in a directory. | `chown -R user1:group1 /home/user1` |
| `--reference=file` | Change ownership to match another file. | `chown --reference=example.txt file.txt` |
| `-v` | Verbose output (show changes made). | `chown -v user1 file.txt` |
| `-c` | Like `-v`, but only show changes. | `chown -c user1 file.txt` |

## `stat` Display's all the information
```sh
dhyanesh@dhyanesh-ThinkPad-T14s-Gen-1:~/Desktop/OS_revision/Commands$ stat File_transfer.md 
  File: File_transfer.md
  Size: 302       	Blocks: 8          IO Block: 4096   regular file
Device: 10302h/66306d	Inode: 12719629    Links: 1
Access: (0664/-rw-rw-r--)  Uid: ( 1000/dhyanesh)   Gid: ( 1000/dhyanesh)
Access: 2025-01-29 12:08:04.390140367 +0530
Modify: 2025-01-29 12:08:04.370140396 +0530
Change: 2025-01-29 12:08:04.370140396 +0530
 Birth: -
```

## `getfacl`/`setfacl` Get and set ACL (Access Control List) permissions.

```sh
dhyanesh@dhyanesh-ThinkPad-T14s-Gen-1:~/Desktop/OS_revision/Commands$ getfacl ./File_transfer.md 
# file: File_transfer.md
# owner: dhyanesh
# group: dhyanesh
user::rw-
group::rw-
other::r--
```




