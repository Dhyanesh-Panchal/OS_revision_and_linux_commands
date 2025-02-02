# Inode:
- An inode (index node) is a data structure used by the Linux filesystem to store metadata about a file.
- Every file in a Linux filesystem has an associated inode, which contains information about the file except for its name and content.
- Each filesystem mounted to your computer has its own inodes.
- The theoretical maximum number of inodes is equal to 2^32 (approximately 4.3 billion inodes).
- Second, and far more important, is the number of inodes on your system. Generally, the ratio of inodes is **1:16KB** of system capacity.
- List inode : `ls -i filename`