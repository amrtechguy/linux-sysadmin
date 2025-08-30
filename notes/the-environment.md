# The Environment

## Notes
- Environment data: `environment variables`, `shell variables`, `aliases`, `shell functions`.

## Examine

```bash
# env vars
printenv
printenv USER

# env vars, shell vars, shell funcs (shell-builtin)
set

# print env and shell vars
echo $HOST

# aliases
alias
alias ls
```

## How it's built

```bash
## login shell
# 1. load
/etc/profile # global
# 2. load one
~/.bash_profile
~/.bash_login
~/.profile # -> load ~/.bashrc

## interactive non-login shell
# 0. inherits the environemt from its parent process (usually a login shell)
# 1. load
/etc/bash.bashrc # global
# 2. load
~/.bashrc # local
```

## Modify

```bash
# reload
source ~/.profile
source ~/.bashrc
```

## Gaps
- [ ] `/etc/profile` vs `/etc/bash.bashrc`.
- [ ] Interactive shell vs Non interactive shell.
- [ ] Using `source` updates the current shell session only or all current user shell sessions?
- [ ] How the environment inheritance works between parent and child processes?