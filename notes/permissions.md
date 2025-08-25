# Permissions

## Notes
- Permissions of files and groups (special user group others).

## Examples

```bash
# rwx -> owner user can (1) list dir (2) create, rename, or delete files inside.
# r-x -> owner group and others can (1) list dir.
drwxr-xr-x

# rwx -> owner user can (1) open and read file (2) modifiy or truncate the content (3) execute it as a program.
# r-x -> owner user and owner group can (1) open and read file (3) execute it as a program.
-rwxr-xr-x

# change file modes
chmod u=rwx,go=rx file.txt
chmod a=rx script.sh

# umask
umask # 0022 `UBUNTU default`
umask 0002 # change the default

# login -> execute -> exit -> output
su -c 'ls -lhi ~' frida

# my privileges
sudo -l

# change ownership user:group
sudo cp users.txt ~frida
sudo chown frida: ~frida/users.txt

# added items' group -> same parent's group
chmod g+s /usr/local/share/Music
```

## Gaps
- [ ] How to apply recursive permissions on dirs only, files only, or all of a dir?
- [ ] Need to understand Special Permissions.
- [ ] How to limit user's access to specific commands?
- [ ] How to use `passwd` to control password aging?