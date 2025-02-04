# `nc`: stands for NetCat.<br>

- `nc` (Netcat) is a powerful networking tool used for reading from and writing to network connections using TCP or UDP. It can be used for a variety of tasks, including port scanning, transferring files, and creating network connections.

| Flag          | Description                                                                                                                                   | Example Usage                             |
|---------------|-----------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------|
| `-l`          | Listen mode. In this mode, `nc` will wait for an incoming connection on the specified port.                                                     | `nc -l 1234`                              |
| `-u`          | Use UDP instead of TCP (the default).                                                                                                           | `nc -u -l 1234`                           |
| `-v`          | Verbose mode. Displays more information, including error messages.                                                                             | `nc -v -l 1234`                           |
| `-n`          | Numeric-only IP addresses, skip DNS resolution.                                                                                               | `nc -n -l 1234`                           |
| `-z`          | Zero I/O mode. This mode is used for scanning without sending any data. Useful for scanning open ports.                                          | `nc -z -v 192.168.1.1 80-100`             |
| `-w`          | Timeout in seconds. Set the timeout for connection establishment or reading data.                                                               | `nc -w 3 192.168.1.1 80`                  |
| `-p`          | Local port number. Bind to a specific local port.                                                                                             | `nc -p 12345 -l`                          |
| `-s`          | Specify the local address to use for outgoing connections.                                                                                      | `nc -s 192.168.1.10 80`                   |
| `-k`          | Keep the listening socket open after the connection is closed. Useful for multiple connections.                                                  | `nc -lk 1234`                             |
| `-c`          | Used to execute a command after the connection is established.                                                                                 | `nc -c 'echo hello' 192.168.1.1 1234`     |
| `-e`          | Specify a program to execute after a successful connection (not available in all versions).                                                     | `nc -e /bin/sh 192.168.1.1 1234`          |
| `-d`          | Detach from stdin and run in the background. Useful for creating a background listener.                                                        | `nc -d -l 1234`                           |
| `-A`          | IPv6. Used to specify that IPv6 should be used for the connection.                                                                             | `nc -A 2001:db8::1 1234`                  |
| `-C`          | Send CRLF after each line (useful for compatibility with some protocols).                                                                      | `nc -C 192.168.1.1 1234`                  |
| `-b`          | Allow broadcasting. Useful for UDP-based broadcast.                                                                                           | `nc -u -b 192.168.1.255 1234`             |


### Testing ports:
```sh
# Check if port 80 is open
nc -zv example.com 80

# Check multiple ports
nc -zv example.com 20-25

# UDP port scanning
nc -zuv example.com 53
``` 

### File Transfer:
```sh
# On receiving machine
nc -l 1234 > received_file.txt

# On sending machine
nc 192.168.1.100 1234 < file_to_send.txt
```

