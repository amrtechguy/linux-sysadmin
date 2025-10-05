# LINUX: SSH

**Notes**
- 

## Install & Enable

```bash
apt install openssh-client
apt install openssh-server

ufw app list
ufw status

ufw allow OpenSSH
ufw enable
ufw status

ufw deny OpenSSH

# the established sshd connection didn't stop after using `ufw deny OpenSSH`,
# so I killed the sshd session process that was handling the connection,
# then all related process was terminated and connection was closed.
```