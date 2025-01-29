# `dstat` Command Documentation

The `dstat` command is an improved version of vmstat that provides better organized and more comprehensive system statistics.

## Basic Usage
```sh
dhyanesh@dhyanesh-ThinkPad-T14s-Gen-1:~/Desktop$ dstat -t -c -m -d -g -n -r -p -l
----system---- --total-cpu-usage-- ------memory-usage----- -dsk/total- ---paging-- -net/total- --io/total- ---procs--- ---load-avg---
        time     |usr sys idl wai stl| used  free  buff  cach| read  writ|  in   out | recv  send| read  writ|run blk new| 1m   5m  15m 
29-01 13:47:30|  4   1  95   0   0|7353M 3863M  423M 5083M|  54k  444k|   0     0 |   0     0 |1.38  8.03 |  0   0 0.2|0.52 0.48 0.55
29-01 13:47:31|  1   1  98   0   0|7351M 3866M  423M 5092M|   0     0 |   0     0 |2214B  694B|   0     0 |2.0   0   0|0.52 0.48 0.55
29-01 13:47:32|  2   1  97   0   0|7374M 3843M  423M 5091M|   0     0 |   0     0 |3323B    0 |   0     0 |  0   0   0|0.52 0.48 0.55
29-01 13:47:33|  1   1  98   0   0|7367M 3850M  423M 5083M|   0     0 |   0     0 | 939B    0 |   0     0 |  0   0   0|0.47 0.47 0.55
29-01 13:47:34|  2   2  96   0   0|7367M 3850M  423M 5084M|   0     0 |   0     0 | 606B   86B|   0     0 |1.0   0   0|0.47 0.47 0.55
29-01 13:47:35|  4   1  95   0   0|7372M 3845M  423M 5084M|   0  7888k|   0     0 |1614B    0 |   0   358 |  0   0   0|0.47 0.47 0.55
29-01 13:47:36|  1   1  97   0   0|7368M 3848M  423M 5084M|   0     0 |   0     0 | 959B  282B|   0     0 |  0   0   0|0.47 0.47 0.55
29-01 13:47:37|  1   1  99   0   0|7359M 3857M  423M 5084M|   0     0 |   0     0 | 660B    0 |   0     0 |  0   0   0|0.47 0.47 0.55
29-01 13:47:38|  2   1  97   0   0|7351M 3866M  423M 5083M|   0     0 |   0     0 |1410B  172B|   0     0 |  0   0   0|0.52 0.48 0.55
29-01 13:47:39|  2   1  98   0   0|7370M 3847M  423M 5083M|   0     0 |   0     0 | 873B    0 |   0     0 |  0   0   0|0.52 0.48 0.55
29-01 13:47:40|  2   0  98   0   0|7367M 3849M  423M 5083M|   0  5544k|   0     0 |1251B    0 |   0  34.0 |  0   0 1.0|0.52 0.48 0.55
```

## Output Measurements
- **dsk/total**: Measured in KB/s
- **paging**: Measured in pages/sec
- **net/total**: Measured in bytes/sec
- **I/O**: Measured in KB/s

## Common Options
- `-t`: Show timestamp
- `-c`: Show CPU stats
- `-m`: Show memory stats
- `-d`: Show disk stats
- `-g`: Show page stats
- `-n`: Show network stats
- `-r`: Show I/O stats
- `-p`: Show process stats
- `-l`: Show load average