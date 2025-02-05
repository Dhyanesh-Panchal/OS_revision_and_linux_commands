# File editing and Interactions.

## 1. `nano`
- `nano` is a lightweight command-line text editor.
- nano uses keyboard shortcuts instead of menus. These shortcuts are displayed at the bottom of the editor:
    - `^` (caret) means "`Ctrl`", so `^X` means `Ctrl + X`.
    - `M`- (Meta) usually means "`Alt`", so `M-U` means `Alt + U`.
- `Ctrl+W` can be used to search word.
#### Configuring `nano`
- Create config file at home: `nano ~/.nanorc`
- Add config, Eg:
```sh
set autoindent   # Enable auto-indent
set tabsize 4    # Set tab width to 4 spaces
set mouse        # Enable mouse support
```

- #### Open file at specific line: `nano +30 file`, will open file at line 30.
- #### Open file in read-only mode: `nano -v file`

## 2. `less`
- `less` is a terminal pager that allows you to **view** large files **page by page** instead of loading them entirely into memory. Unlike `cat`, it does not load the entire file at once, making it efficient for large files like logs.
- we can use `/` to find and highlight keywords.

| Key     | Action                                      |
|---------|---------------------------------------------|
| Space   | Move down one screen                        |
| `b`     | Move up one screen                          |
| Enter   | Move down one line                          |
| `y`     | Move up one line                            |
| `g`     | Go to the beginning of the file             |
| `G`     | Go to the end of the file                   |
| `n`     | Repeat last search in the same direction    |
| `N`     | Repeat last search in the opposite direction|
| `q`     | Quit `less`                                 | 


#### Options in less:
| Flag | Description                                                                 |
|------|-----------------------------------------------------------------------------|
| `-i` | Case-insensitive search.                                                   |
| `-p` | Search for and highlight the first occurrence of a pattern immediately upon opening. |
| `-n` | Show the current line number while scrolling.                               |
| `-N` | Show line numbers on the left.                                             |
| `-g` | Skip past all instances of the search pattern.                             |
| `-s` | Use regular expressions for searches.                                      |