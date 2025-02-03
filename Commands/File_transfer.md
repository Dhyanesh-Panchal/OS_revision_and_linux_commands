# File transfer commands.


## 1. `scp`: (Secure Copy Protocol) command is used to securely transfer files and directories between local and remote hosts over SSH (Secure Shell). 
<br>``scp [options] <source> <destination>``
- Copying from remote to local:<br>
``scp user@remote_host:/remote/directory/file.txt /local/directory/``
-  Copy a file from local to remote
``scp file.txt user@remote_host:/path/to/destination/``
- Copy a directory recursively:
``scp -r local_directory/ user@remote_host:/remote/path/``
- Use a specific SSH key for authentication
``scp -i /path/to/private_key file.txt user@remote_host:/path/``
- If the remote has SSH service on different port, use `-P` to specify the SSH port.

### `scp` when connected under VPN.
 

| Option | Description                                      |
|--------|--------------------------------------------------|
| `-r`   | Copy directories recursively                     |
| `-P`   | Specify SSH port (uppercase `-P`)                |
| `-i`   | Use a specific identity (private key) file       |
| `-l`   | Limit bandwidth (in Kbit/s)                      |
| `-C`   | Enable compression                               |
| `-q`   | Suppress progress meter and non-error messages   |
| `-v`   | Enable verbose mode (useful for debugging)       |

### 


## 2. `sftp` Secure File Transfer Protocol
- `sftp` is an interactive command-line tool that allows secure file transfers between a local and a remote system over SSH.
- Unlike `scp`, `sftp` provides an interactive session where users can navigate directories and perform file operations.
- ``sftp user@remote_host`` can be used to connect to remote server.
- ``sftp -i /path/to/private_key user@remote_host`` for private key Authentication.
| Command            | Description                                      |
|--------------------|--------------------------------------------------|
| `get <file>`       | Download a file from remote to local             |
| `put <file>`       | Upload a file from local to remote               |
| `mget <files>`     | Download multiple files                          |
| `mput <files>`     | Upload multiple files                            |
| `ls`               | List remote directory contents                   |
| `cd <dir>`         | Change remote directory                          |
| `lcd <dir>`        | Change local directory                           |
| `pwd`              | Print remote working directory                   |
| `lpwd`             | Print local working directory                    |
| `rm <file>`        | Remove a remote file                             |
| `mkdir <dir>`      | Create a remote directory                        |
| `rmdir <dir>`      | Remove a remote directory                        |
| `exit` or `bye`    | Close the SFTP session                           |