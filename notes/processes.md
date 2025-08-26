# Processes


## View

```bash
# all processes + rich properties
ps aux

# 
pstree

# top processes
# press `f` to filter -> select (%CPU, %MEM, or ...) -> press `s` -> ESC
top

#
htop
```

## Control

```bash
xlogo

# interrupt or terminate
CTRL+C

# run in the bg
xlogo &

jobs

fg %1

# stop or pause -> bg
CTRL+Z

# resume -> bg
bg %1
```

## Gaps
- [ ] What is the process vs program?
- [ ] Does any program or script on linux run through the shell?
- [ ] TTY vs pts/0.
- [ ] What is `controlling terminal`?
- [ ] What is `BSD-style` behavior or command?
- [ ] Need explanation to the columns.

```bash
USER         PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root           1  0.0  0.4  25272 15636 ?        Ss   14:40   0:15 /sbin/init auto automatic-ubiquity noprompt
```

- [ ] Explain `load average: 0.03, 0.03, 0.00`, and `4.5 us` vs  `3.7 sy`.

```bash
top - 21:31:59 up  6:51,  2 users,  load average: 0.03, 0.03, 0.00
Tasks: 297 total,   1 running, 296 sleeping,   0 stopped,   0 zombie
%Cpu(s):  4.5 us,  3.7 sy,  0.0 ni, 91.8 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st 
MiB Mem :   3354.4 total,    713.1 free,   1439.5 used,   1520.0 buff/cache     
MiB Swap:   3530.0 total,   3530.0 free,      0.0 used.   1914.9 avail Mem 
```
