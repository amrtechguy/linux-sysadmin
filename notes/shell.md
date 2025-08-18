# What is the shell?

## Overview
- Understanding the shell and how it works.

## Key Points
- `Shell` is a program that takes commands and passes them to the kernel through system calls to execute.
- `sh` is the orignal Unix shell written by ***Stephen Bourne***.
- `bash` is the replacement for the Unix shell `sh`. It was developed by the GNU project and used by default on most Linux distros.
- The `terminal emulator` is the GUI program that emulates the old physical terminal that takes keystrokes from the user and passes them to the shell.
- `TTY` is the virtual text console provided by the Linux kernel. Unlike the `terminal emulator` (which runs inside a GUI), a `TTY` runs independently of the graphical environment.
- Linux has multiple `TTYs`. To switch between them, use `CTRL+ALT+F2-F6` on most modern linux distros.
- The `Linux desktop session` runs on top of a `TTY`.

## Commands
- The shell prompt
  ```bash
  user@linux:~$
  ```
  > `user` is the logged in username.\
  > `linux` is the machine name.\
  > `$` refers to a normal user.

- The shell prompt of the superuser who has root privileges
  ```bash
  user@linux:~#
  ```
  > `#` refers to the root user.

- `date` displays the current time and date.
  ```bash
  user@linux:~$ date
  Sun Aug 17 07:01:08 PM EEST 2025
  ```

- `df` displays the free and used space on the disk drives.
  ```bash
  user@linux:~$ df
  Filesystem     1K-blocks     Used Available Use% Mounted on
  tmpfs             343504     2116    341388   1% /run
  /dev/sda2       20463184 13554696   5843684  70% /
  tmpfs            1717504        0   1717504   0% /dev/shm
  tmpfs               5120        8      5112   1% /run/lock
  tmpfs               1024        0      1024   0% /run/credentials/systemd-journald.service
  tmpfs            1717508       28   1717480   1% /tmp
  tmpfs               1024        0      1024   0% /run/credentials/systemd-resolved.service
  tmpfs             343500      124    343376   1% /run/user/1000
  /dev/sr0          101838   101838         0 100% /media/amr/CDROM
  /dev/sr1         6131368  6131368         0 100% /media/amr/Ubuntu 25.04 amd64
  tmpfs               1024        0      1024   0% /run/credentials/getty@tty3.service
  tmpfs               1024        0      1024   0% /run/credentials/getty@tty6.service
  ```

- `free` displays amount of free and used memory in the system.
  ```bash
  user@linux:~$ free
                  total        used        free      shared  buff/cache   available
  Mem:         3435012     1400624      438660       34996     1917868     2034388
  Swap:        3614716         248     3614468
  ```

- `exit` or `CTRL-D` ends the current terminal session.
  ```bash
  user@linux:~$ exit
  ```
