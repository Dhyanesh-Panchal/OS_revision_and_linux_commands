## File Compression and Archiving Commands

| Command  | Description | Example |
|----------|------------|---------|
| `tar`    | Create and extract archive files. | `tar -cvf archive.tar file1 file2` (Create `.tar` archive) |
| `zip`    | Compress files into a ZIP archive. | `zip archive.zip file1 file2` |
| `unzip`  | Extract files from a ZIP archive. | `unzip archive.zip` |
| `gzip`   | Compress a file using Gzip. | `gzip file.txt` (Creates `file.txt.gz`) |
| `gunzip` | Decompress a Gzip-compressed file. | `gunzip file.txt.gz` |
| `bzip2`  | Compress a file using Bzip2. | `bzip2 file.txt` (Creates `file.txt.bz2`) |
| `bunzip2`| Decompress a Bzip2-compressed file. | `bunzip2 file.txt.bz2` |
| `xz`     | Compress a file using XZ. | `xz file.txt` (Creates `file.txt.xz`) |
| `unxz`   | Decompress an XZ-compressed file. | `unxz file.txt.xz` |
| `7z`     | Create and extract 7-Zip archives. | `7z a archive.7z file1 file2` |


## `tar` and `zip`/`unzip` with flags.
| Command  | Description | Example |
|----------|------------|---------|
| `tar -cvf archive.tar file1 file2` | Create a tar archive. | `tar -cvf backup.tar file1.txt file2.txt` |
| `tar -xvf archive.tar` | Extract files from a tar archive. | `tar -xvf backup.tar` |
| `tar -tvf archive.tar` | List contents of a tar archive. | `tar -tvf backup.tar` |
| `zip archive.zip file1 file2` | Compress files into a ZIP archive. | `zip myfiles.zip file1.txt file2.txt` |
| `zip -r archive.zip directory/` | Compress a directory into a ZIP file. | `zip -r project.zip /home/user/project` |
| `unzip archive.zip` | Extract files from a ZIP archive. | `unzip myfiles.zip` |
| `unzip -l archive.zip` | List contents of a ZIP file. | `unzip -l myfiles.zip` |
| `unzip archive.zip -d /path/to/destination` | Extract ZIP file to a specific directory. | `unzip myfiles.zip -d /home/user/Documents` |