# `top` and `htop` Commands Documentation

Both `top` and `htop` are real-time system monitoring tools that display system processes, resource usage, and performance metrics.

## top Command
![top](../../Images/top.png)
### Process States
- Running (R)
- Sleeping (S)
- UnInterruptable Sleep (D)
- Suspended processes (T)
- Zombie (Z)

### CPU Time Categories
- User mode (us)
- System mode (sy)
- Nice mode (ni)
- Idle (id)
- Waiting for I/O (wa)
- Hardware interrupts (hi)
- Software interrupts (si)
- Steal time (st)

### Process Information Fields
- **PID**: Process ID
- **USER**: User owning the process
- **PR**: Process priority (PR = 20 + NI)
- **NI**: Nice value (priority modifier)
- **VIRT**: Virtual memory used by the process
- **RES**: Resident memory (physical memory) used by the process
- **SHR**: Shared memory used by the process
- **S**: Process state
- **%CPU**: CPU usage of the process
- **%MEM**: Memory usage of the process
- **TIME+**: Total CPU time consumed by the process
- **COMMAND**: Command or name of the process

## htop Command
![htop](../../Images/htop.png)

htop is an improved version of top with additional features:
- Interactive process viewer
- Visual color-coded indicators
- Horizontal and vertical process views
- Better handling of process sorting
- Built-in kill command
