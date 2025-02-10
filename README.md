# Operating System Documentation

## Table of Contents
1. [Linux Commands](#linux-commands)
2. [System Concepts](#system-concepts)
3. [Command Categories](#command-categories)

## Linux Commands

### Command Categories

#### File Operations
- Basic File Management
  - [Basic File Commands](Commands/Files/basic_file_management.md)
  - [File Permissions](Commands/Files/File_permissions.md)
  - [File Systems](Commands/Files/filesystems.md)
  - [Compression & Decompression](Commands/Files/file_compression_decompression.md)
  - [Text Editors & Interactions](Commands/Files/Editors_and_Interactions.md)
- [File Transfer Commands](Commands/File_transfer.md)

#### System Resources
- CPU Management
  - [CPU Information Commands](Commands/CPU_details/cpu_info.md)
- Memory Management
  - [Virtual Memory Overview](Commands/Memory/Virtual_memory.md)
  - [Free Command](Commands/Memory/free.md)
  - [VMStat Command](Commands/Memory/vmstat.md)
  - [DStat Command](Commands/Memory/dstat.md)
- Disk Operations
  - [df - Disk Free Space](Commands/Disk/df.md)
  - [du - Disk Usage](Commands/Disk/du.md)
  - [fdisk - Partition Manager](Commands/Disk/fdisk.md)
  - [lsblk - List Block Devices](Commands/Disk/lsblk.md)
- Process Management
  - [PS Command](Commands/Process/ps.md)
  - [Top & Htop](Commands/Process/top_htop.md)
  - [Process Control](Commands/Process/process_control.md)

#### Networking
- [Netcat (nc) Command](Commands/Networking/nc.md)
- [Socket Statistics (ss)](Commands/Networking/ss.md)

#### Special Topics
- [Process Information (/proc folder)](Commands/proc_folder.md)
- [Selection and Sorting Commands](Commands/Selection_sorting_commands/)
- [Other Useful Commands](Commands/other_usefull.md)

### Common Commands Quick Reference

#### File and Directory Operations
- `ls` - List directory contents
- `cd` - Change directory
- `pwd` - Print working directory
- `mkdir` - Create a new directory
- `rm` - Remove files or directories
- `cp` - Copy files or directories
- `mv` - Move or rename files

#### File Viewing
- `cat` - Display file contents
- `less` - View file contents page by page
- `head` - Display first few lines of a file
- `tail` - Display last few lines of a file

#### System Information
- `top` - Display system processes
- `df` - Show disk space usage
- `free` - Display memory usage
- `uname` - Show system information

#### File Permissions
- `chmod` - Change file permissions
- `chown` - Change file owner

## Note
Each linked directory contains detailed documentation about specific commands and their usage. Please refer to the individual files for comprehensive information about each category of commands.
