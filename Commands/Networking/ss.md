# `ss` (Socket Statistics):
- Its a used to display information about network sockets.
- Updated version of `netstat`.

| Flag | Description                                                                 |
|------|-----------------------------------------------------------------------------|
| `-l` | Display listening sockets only (TCP or UDP ports waiting for connections). |
| `-t` | Show only TCP sockets.                                                      |
| `-u` | Show only UDP sockets.                                                      |
| `-a` | Display all sockets (including non-listening).                              |
| `-n` | Show numerical addresses instead of resolving hostnames.                    |
| `-p` | Show the process using the socket. Requires root privileges.                 |
| `-r` | Resolve service names for port numbers (e.g., 80 → http).                    |
| `-s` | Display socket summary statistics.                                          |
| `-4` | Display IPv4 sockets only.                                                 |
| `-6` | Display IPv6 sockets only.                                                 |
| `-w` | Display raw socket information.                                             |
| `-o` | Show timers (e.g., retransmit and timeout).                                 |
| `-H` | Suppress the display of the column headers.                                 |
| `-I` | Display detailed information on socket interface (e.g., link-layer details). |

## Example `ss -tuln`

### **Output Description:**
When running the `ss` command, the output typically includes the following columns:
1. **Netid**: 
   - The type of socket (e.g., `tcp`, `udp`, `unix`, etc.).

2. **State**: 
   - The current state of the socket. Common states include:
     - `LISTEN`: The socket is waiting for incoming connections.
     - `ESTABLISHED`: The connection is established and data can be transferred.
     - `CLOSE_WAIT`: The remote end has closed the connection, and the local system is waiting to close it.
     - `TIME_WAIT`: The socket is waiting for all packets to be acknowledged before being closed.
     - `SYN_SENT`: The connection request has been sent, and the system is waiting for acknowledgment.
     - `CLOSED`: The socket is closed.
     - Other states may appear depending on the connection.

3. **Recv-Q**: 
   - The size of the **receive queue**. Represents the number of bytes waiting to be read by the application from the socket. If this value is large, it may indicate that the application is not reading the incoming data fast enough.

4. **Send-Q**: 
   - The size of the **send queue**. Represents the number of bytes waiting to be transmitted by the kernel. If this value is large, it may indicate that the system is sending data faster than it can be transmitted.

5. **Local Address:Port**: 
   - The local IP address and port number associated with the socket. This shows where the socket is bound on the local machine. For example, `0.0.0.0:ssh` would indicate that the system is listening for SSH connections on all interfaces.

6. **Peer Address:Port**: 
   - The remote (peer) address and port associated with the socket, indicating the destination for the connection (for established connections). If the socket is not connected (e.g., in `LISTEN` state), this will be shown as `*` or `0.0.0.0`.

7. **Process**: 
   - The process name and PID (Process ID) using the socket (if the `-p` flag is used). This helps identify which application or service is using a particular socket. For example, `python3:1234` indicates that a Python process with PID 1234 is using the socket.

---
