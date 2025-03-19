# `grep` (Global Regular Expression Print)

- `grep` is used to search for patterns in files. It supports basic regular expressions.
- Syntax: `grep [OPTIONS] PATTERN [FILE...]`

| Option | Description                                      |
|--------|--------------------------------------------------|
| `-i`   | Ignore case distinctions                         |
| `-v`   | Invert match (show lines that do not match)      |
| `-c`   | Count the number of matching lines               |
| `-l`   | List filenames with matches                      |
| `-n`   | Show line numbers with output                    |
| `-r`   | Search recursively in directories                |
| `-E`   | Use extended regular expressions                 |
| `-F`   | Interpret pattern as a fixed string              |

## Pipelining `grep` with other commands output.
- `ps aux | grep clickhouse` will find all the lines containing clickhouse in it.
- `netstat -an | grep "LISTEN"` lists all the listening states.
- Etc.

