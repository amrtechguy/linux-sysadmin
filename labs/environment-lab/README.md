# Environment Lab

## Tasks

- [x] List all environment variables in your current login shell.

```bash
printenv
```

- [x] Find the values of `$USER`, `$SHELL`, and `$HOME` in your current login shell.

```bash
#echo $USER
printenv USER
#echo $SHELL
printenv SHELL
#echo $HOME
printenv HOME
```

- [x] Temporarily add `~/bin` to `PATH` in the current non-login shell.

```bash
mkdir ~/bin
PATH=$PATH":$HOME/bin"
```

- [x] Make a variable `PROJECT="lab"` available to child shells.

```bash
export PROJECT="lab"
bash
echo $PROJECT
```

- [x] For the current user, add a permanent alias `cls` that clears the screen.

```bash
nano ~/.bashrc
alias cls='clear' # add to `~/.bashrc`
```

- [x] Add `/srv/scripts` permanently to `PATH` for all users at login.

```bash
sudo mkdir /srv/scripts
sudo cp /etc/profile /etc/profile.bak
sudo nano /etc/profile
PATH="$PATH:/srv/scripts"
source ~/.profile
```

- [x] Set a default editor variable `EDITOR=nano` only for your user at login.

```bash
nano ~/.profile
EDITOR=nano
```

## Notes:
- `PROJECT="lab"`: could not be read by `printenv`, but was read by `echo $PROJECT`.
    - `printenv` reads the environment variables.
    - `echo $PROJECT` reads from the shell variables.