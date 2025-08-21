# Commands

## Notes
- ...

## Command Info

```bash
# command type.
type cd

# for builtin commands.
help cd

# --help option. (not always)
mv --help

# -h option. (not always)
useradd -h

# section 1 -> command manual page . (not always)
man 1 passwd

# one-line command description.
whatis cp

# command info.
# Note: `info` of GNU Project replacement to `man` of Unix.
info cp
```

## Command Finding

```bash
# path(s) of executable.
which cp

# path(s) of executable's binaries, man pages, ...
whereis cp

# search in man pages.
apropos disk blocks

# search in man pages.
man -k disk blocks
```

## Alias Command
```bash
# define a command alias. 
alias foo="ls -la ~"

# lists contents of user's home 
foo
```

## Gaps
- [ ] ...