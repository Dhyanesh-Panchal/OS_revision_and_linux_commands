# Basic File management commands

| Command  | Description | Example |
|----------|------------|---------|
| `ls`     | List files and directories. | `ls -la` (Show all files with details) |
| `pwd`    | Print the current working directory. | `pwd` (Displays the current path) |
| `cd`     | Change directory. | `cd /home/user/Documents` |
| `mkdir`  | Create a new directory. | `mkdir new_folder` |
| `rmdir`  | Remove an empty directory. | `rmdir old_folder` |
| `rm`     | Remove files or directories. | `rm -rf folder_name` (Delete folder recursively) |
| `touch`  | Create an empty file or update timestamp. | `touch file.txt` |
| `cp`     | Copy files or directories. | `cp file.txt /backup/` |
| `mv`     | Move or rename files and directories. | `mv old.txt new.txt` (Rename file) |
| `find`   | Search for files and directories. | `find / -name "*.log"` (Find all `.log` files) |
| `tree`   | Display directory structure in a tree-like format. | `tree /home/user` |


## `find`
The `find` command in Linux is used to search for files and directories in a directory hierarchy based on various criteria such as name, size, type, modification time, and permissions.
Syntax: `find [path] [expression]`

