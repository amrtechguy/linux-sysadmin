# Processes

## View

```bash
ps aux # all processes + rich properties
pstree
top # press `f` to filter -> select (%CPU, %MEM, or ...) -> press `s` -> ESC
htop
vmstat # system resources
tload

## process selection
ps -e # all
ps -u $USER
ps -C "bash" # command name(s)
ps -p 1,2,3 # PID
ps --ppid 2235 # PPID
ps -t "1 2" # TTY

## output format
ps -f # full format
ps -l # long format
ps -o user,pid,ppid,%cpu,%mem,tty,state,cmd # select columns

## pstree
pstree  -ps 3245 # parents tree + pid
```

## Jobs

```bash
xlogo # a testing GUI program
CTRL+C # interrupt or terminate
xlogo & # run in the bg
jobs
fg %1
CTRL+Z # stop or pause -> bg
bg %1 # resume -> bg
```

## Kill

```bash
kill -INT 3800 # CTRL-C
kill -KILL 3800 # kernel's
kill -TERM 3800 # default
kill -CONT 3800 
kill -STOP 3800 # kernel's
kill -TSTP 3800

# safe
kill 3800 # doesn't affect `stopped` programs

# aggressive
kill -KILL 3800

killall -u user -TERM xlogo
```

## Shutting down

```bash
shutdown -r 22:00 # reboot @ 10:00 P.M
shutdown -H +5 # halt after 5 minutes
shutdown -P now # power off now
shutdown -P # default time +1
```

## Gaps
- [ ] process vs program.
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

- [ ] Need to understand the differences between the `kill` signals.
- [ ] Signals sent to programs vs others don't.
- [ ] When the program is `stopped` can it still receive signals or need to be `continued` first?

- [ ] `+` vs `-`.

```bash
user@linux:~$ jobs
[1]+  Stopped                 xlogo
[2]   Running                 xlogo &
[3]-  Running                 xlogo &
```

- [ ] Explain.

```bash
user@linux:~$ vmstat
procs -----------memory---------- ---swap-- -----io---- -system-- -------cpu-------
 r  b   swpd   free   buff  cache   si   so    bi    bo   in   cs us sy id wa st gu
 3  0      0 761148 157432 1378656    0    0   123    12  251    1  2  2 95  1  0  0
```