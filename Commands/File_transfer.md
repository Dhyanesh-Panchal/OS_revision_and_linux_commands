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


| Option | Description                                      |
|--------|--------------------------------------------------|
| `-r`   | Copy directories recursively                     |
| `-P`   | Specify SSH port (uppercase `-P`)                |
| `-i`   | Use a specific identity (private key) file       |
| `-l`   | Limit bandwidth (in Kbit/s)                      |
| `-C`   | Enable compression                               |
| `-q`   | Suppress progress meter and non-error messages   |
| `-v`   | Enable verbose mode (useful for debugging)       |


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
```sh
hyanesh@dhyanesh-ThinkPad-T14s-Gen-1:~/Desktop/test_go$ sftp maulikpuri@10.20.40.171
maulikpuri@10.20.40.171's password: 
Connected to 10.20.40.171.
sftp> pwd
Remote working directory: /home/maulikpuri
sftp> ls
Desktop                                                Documents                                              Downloads                                              
Music                                                  Pictures                                               Public                                                 
Templates                                              Videos                                                 bb.txt                                                 
clickhouse                                             clickhouse-client-24.12.3.47                           clickhouse-client-24.12.3.47-amd64.tgz                 
clickhouse-common-static-24.12.3.47                    clickhouse-common-static-24.12.3.47-amd64.tgz          clickhouse-common-static-dbg-24.12.3.47                
clickhouse-common-static-dbg-24.12.3.47-amd64.tgz      clickhouse-keeper-24.12.3.47-amd64.tgz                 clickhouse-server-24.12.3.47                           
clickhouse-server-24.12.3.47-amd64.tgz                 hello.txt                                              install_clickhouse.sh                                  
new.tar                                                sample.txt                                             sample2.txt                                            
snap                                                   yohooo.txt                                             
sftp> cd Desktop/
sftp> ls
os  
sftp> put ~/Desktop/sample2.txt
stat ~/Desktop/sample2.txt: No such file or directory
sftp> put /home/dhyanesh/Desktop/sample2.txt
Uploading /home/dhyanesh/Desktop/sample2.txt to /home/maulikpuri/Desktop/sample2.txt
/home/dhyanesh/Desktop/sample2.txt                                                                                                  100%  180    40.7KB/s   00:00    
sftp> ls
os           sample2.txt  
sftp> get -r os
Fetching /home/maulikpuri/Desktop/os/ to os
Retrieving /home/maulikpuri/Desktop/os
Retrieving /home/maulikpuri/Desktop/os/.git
Retrieving /home/maulikpuri/Desktop/os/.git/hooks
/home/maulikpuri/Desktop/os/.git/hooks/applypatch-msg.sample                                                                        100%  478    48.6KB/s   00:00    
/home/maulikpuri/Desktop/os/.git/hooks/commit-msg.sample                                                                            100%  896    35.8KB/s   00:00    
/home/maulikpuri/Desktop/os/.git/hooks/update.sample                                                                                100% 3610   332.9KB/s   00:00    
.
.
.
/home/maulikpuri/Desktop/os/Commands/Memory.md                                                                                      100%   21KB   1.4MB/s   00:00    
sftp> exit
exit
```