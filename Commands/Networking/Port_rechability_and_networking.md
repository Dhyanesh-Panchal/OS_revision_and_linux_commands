# Commands for port rechability:
## `netstat` : stands for Network Statistics.<br/>
Options explained:
```sh
-t : Show TCP connections
-u : Show UDP connections
-l : Show only listening ports
-n : Show numerical addresses
-p : Show process/program name (requires root)
-a : Show all sockets
-r : Show routing table
```
Example: ``netstat -tuln``<br>
![alt](../Images/Netstat_tuln.png)
<br>Show statistics for all protocols: `netstat -s`

1. `telnet`: It can be used to verify open **TCP** ports on a remote system.
- `telnet <IP/hostname> <port>` to verify the rechability of the port.
- For e.g.: ``telnet 192.168.29.1 80``

    
