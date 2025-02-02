# `du` Disk Usage
- Displays the disk space usage of files and directories.
- Syntax `du [OPTIONS] [FILE/DIRECTORY]`.
- By default, `du` shows the size of each subdirectory in kilobytes (KB).
```sh
dhyanesh@dhyanesh-ThinkPad-T14s-Gen-1:~$ du | head -n 15
4	./Music
5064	./Pictures
4	./Videos
8	./clickhouse-common-static-24.12.3.47/install
452	./clickhouse-common-static-24.12.3.47/usr/share/doc/clickhouse-common-static
456	./clickhouse-common-static-24.12.3.47/usr/share/doc
120	./clickhouse-common-static-24.12.3.47/usr/share/clickhouse/protos/google/protobuf
124	./clickhouse-common-static-24.12.3.47/usr/share/clickhouse/protos/google
128	./clickhouse-common-static-24.12.3.47/usr/share/clickhouse/protos
132	./clickhouse-common-static-24.12.3.47/usr/share/clickhouse
28	./clickhouse-common-static-24.12.3.47/usr/share/bash-completion/completions
32	./clickhouse-common-static-24.12.3.47/usr/share/bash-completion
624	./clickhouse-common-static-24.12.3.47/usr/share
531768	./clickhouse-common-static-24.12.3.47/usr/bin
532396	./clickhouse-common-static-24.12.3.47/usr
.
.
.
```
- Another example using specific directory.
```sh
dhyanesh@dhyanesh-ThinkPad-T14s-Gen-1:~$ du -h ~/Desktop/OS_revision/
20K	/home/dhyanesh/Desktop/OS_revision/Commands/Disk
28K	/home/dhyanesh/Desktop/OS_revision/Commands/Process
20K	/home/dhyanesh/Desktop/OS_revision/Commands/Memory
88K	/home/dhyanesh/Desktop/OS_revision/Commands
56K	/home/dhyanesh/Desktop/OS_revision/.git/hooks
8.0K	/home/dhyanesh/Desktop/OS_revision/.git/logs/refs/remotes/origin
12K	/home/dhyanesh/Desktop/OS_revision/.git/logs/refs/remotes
8.0K	/home/dhyanesh/Desktop/OS_revision/.git/logs/refs/heads
24K	/home/dhyanesh/Desktop/OS_revision/.git/logs/refs
32K	/home/dhyanesh/Desktop/OS_revision/.git/logs
4.0K	/home/dhyanesh/Desktop/OS_revision/.git/branches
8.0K	/home/dhyanesh/Desktop/OS_revision/.git/refs/remotes/origin
12K	/home/dhyanesh/Desktop/OS_revision/.git/refs/remotes
4.0K	/home/dhyanesh/Desktop/OS_revision/.git/refs/tags
.
.
.
```
- `-s` flag can be used to get the info for the provided dirrctory, Excluding its childs.
```sh
dhyanesh@dhyanesh-ThinkPad-T14s-Gen-1:~$ du -s /home/dhyanesh/Desktop/
2480	/home/dhyanesh/Desktop/
```