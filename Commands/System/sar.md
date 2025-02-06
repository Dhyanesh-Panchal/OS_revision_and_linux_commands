# `sar` System Activity Report
- The `sar` command is used to collect, report, and save system activity information. It can report CPU utilization, memory usage, I/O activity, and much more over time.

| Flag     | Description                                                                 |
|----------|-----------------------------------------------------------------------------|
| `-u`     | Displays CPU utilization report.                                            |
| `-r`     | Reports memory utilization (used, free, swap, etc.).                        |
| `-d`     | Shows device (disk) activity, including reads, writes, and I/O time.        |
| `-n`     | Used for network-related reports like interface statistics.                 |
| `-q`     | Displays queue length, processes in the run queue, and other process metrics.|
| `-B`     | Reports swap space utilization.                                             |
| `-P ALL` | Reports CPU statistics for all processors (when using `-u` flag).           |
| `-s`     | Specifies the interval in seconds between each report.                      |
| `-e`     | Allows you to specify the start and end time for the report.                |
| `-f`     | Collects data in the specified file format.                                 |
| `-h`     | Displays help with usage information.                                       |


