# Searching For Files

## Notes
- `find` is powerful.

## Tools

```bash
updatedb
locate -ie /bin/hosts # insensitive, existing

# tests
find /var/log -type f -size +1M
find /var/log -newer /var/log/syslog
find / -nouser
find / -nogroup
# operators
find /srv \( -type f -not -perm 0600 \) -or \( -type d -not -perm 0700 \)
# predefined actions
find /srv/project -type f -name '*.tmp' -size +1M -print -ls -delete
# user-defined actions
find ./lab2 -type f -name 'dir*' -ok rm '{}' ';'
find ./lab2 -type f -name 'dir*' -exec ls -alh '{}' ';' # multiple ls instances
find ./lab2 -type f -name 'dir*' -exec ls -alh '{}' + # single ls instance

xargs --show-limits
<CTRL-C>

find ./lab2 -type f -name 'dir*' | xargs ls -alh
find ./lab2 -type f -name 'dir*' -print0 | xargs --null ls -alh

find / -mount \( -type f -not -perm 0600 \) -or \( -type d -not -perm 0700 \) # avoid mounted filesystems
find / -noleaf -type f -name 'secret.txt' # no optimize for non-unix filesystem
```

## Gaps
- [ ] What are the safe permissions for files and dirs?
- [ ] Does Linux allow `null` char in file/dir names?
- [ ] The difference between `Access`, `Modify`, `Change`, `Birth`.

```bash
user@linux:/srv/rabbit$ sudo stat timestamp 
  File: timestamp
  Size: 0         	Blocks: 0          IO Block: 4096   regular empty file
Device: 8,2	Inode: 658092      Links: 1
Access: (0644/-rw-r--r--)  Uid: (    0/    root)   Gid: (    0/    root)
Access: 2025-09-07 19:06:08.780805116 +0300
Modify: 2025-09-07 19:06:08.780805116 +0300
Change: 2025-09-07 19:06:08.780805116 +0300
Birth: 2025-09-07 19:04:34.535417957 +0300
```
