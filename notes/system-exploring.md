# Exploring the system

## Overview
- A quick description of what the topic is and why it matters (just 2–3 lines).

## Main Points

### 1. Linux commands format
- It's influenced by the GNU project.
- Most commands have options and accept arguments.
- The names of commands and options are case sensitive.
```bash
# short options
command -options arguments

# long options
command --long-option arguments
```

### 2. `ls` command
- Used for listing the contents of dirictories.
- It uses the current directory by default, unless a different directory is passed as an argument.
- Here's a list of common `ls` options:
| Command | Note |
| --- | --- |
| ls | lists the contents of the current working directory in an ascending alphabetical order |
| ls / ~ | lists the contents of multiple directories of the root '/' and the user's home directory '~' |
| ls -ld | `d` lists the directory itself, not its contents. `l` displays its info. |
| ls -a | lists all contents including the virtual directories of current directory '.' and its parent directory '..' |
| ls -A | lists all contents excluding the virtual directories of current directory '.' and its parent directory '..' |
| ls -F | acts like `-A`, but classify each content with a symbol or a character at its end to refer to its type e.g. `*` refers to an executable file and `/` refers to a directory |
| ls -l | lists the contents in long format that displays more info about the directory contents |
| ls -lh | the option 'h' is used with -l to display file sizes in a human readable format |
| ls -sh | using the option `s` with `h` to display the allocated size for each file in a human readable format. |
| ls -S | lists the contents sorted by the size |
| ls -r | lists the contents in a reverse order |
| ls -t | lists the contents sorted by last modification date and time |

- Example on a file's attributes displayed by the command `ls -l`.
```bash
-rw-r--r-- 1 user group  307 Jul 27 19:29 users.txt
```
> `-` the file type.\
> `rw-` the permissions or access rights of the user who owns the file.\
> `r--` the permissions or access rights of the group who owns the file.\
> `r--` the permissions or access rights of all other users.\
> `1` the number of hard links that the file has.\
> `user` the name of the user who owns the file.\
> `group` the name of the group that owns the fie.\
> `307` the file size in bytes.\
> `Jul 27 19:29` the last modification date and time of the file.\
> `users.txt` the name of the file.

### 3. `file` command
- Used for determining a file's type.
```bash
# used with an ASCII text file
user@linux:~$ file users.txt
users.txt: ASCII text

# used with a binary executable file
user@linux:~$ file /usr/sbin/useradd
/usr/sbin/useradd: ELF 64-bit LSB pie executable, x86-64, version 1 (SYSV), dynamically linked, interpreter /lib64/ld-linux-x86-64.so.2, BuildID[sha1]=304433f3cd541533fbbe4c908fd9538066d732a7, for GNU/Linux 3.2.0, stripped
```

## Examples

## Questions
