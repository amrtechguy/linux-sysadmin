# Archiving and Backup

## Notes
- compression techniques: `lossy` -> (JPEG, MP3) vs `lossless`.
- archiving: `tar`.
- compressing: `gzip`, `gunzip`.
- synchronizing: `rsync`.

## Compression

```bash
gzip foo.txt
gunzip foo.txt.gz

ls -alh /etc | gzip > foo.txt.gz

zcat foo.txt.gz
zless foo.txt.gz

bzip2 foo.txt
bunzip2 foo.txt.bz2
bzip2recover foo.txt.bz2

bzcat foo.txt.bz2
bzless foo.txt.bz2
```

## Archiving

```bash
tar -cvf /mnt/backup_disk/home.tar /home

cd /
tar -xvf /mnt/backup_disk/home.tar

tar -xf playground.tar --wildcards 'playground/dir-*/file-A'

find playground/ -name 'file-A' -exec tar rf playground.tar '{}' '+'

find playground/ -name 'file-A' | tar -cf - --files-from=- | gzip > playground.tar.gz # .tgz, .tar.gz

find playground -name 'file-A' | tar -czf - -T - > playground.tgz # z -> gzip
find playground -name 'file-A' | tar -cjf - -T - > playground.tbz # j -> bzip2

tar -czf home_backup.tgz /home

ssh frida@localhost 'tar -cf - ~' | tar -xf -

zip -r my_home_backup.zip ~
unzip -l my_home_backup.zip
unzip my_home_backup.zip
```

## Synchronizing Files and Directories

```bash
rm -rf foo/*
rsync -av playground foo
rsync -av playground/ playground_backup

rsync -av --delete /etc /home /usr/local /media/user/backup_drive
rsync -av --delete --rsh=ssh playground backup@backupserver:/backup
rsync -av --delete rsync://archive.linux.duke.edu/fedora/linux/development/rawhide/Everything/x86_64/os/ fedora
```

## Gaps
- [ ] `ls -l | gzip -c` vs `gzip -dc foo.txt.gz`. Is the command's `stdin` different from its passed `arguments`?
- [ ] Understand `tar -cf - --files-from=-`.
- [ ] Understand `zip`, `unzip`.
- [ ] How to configure `rsync` as a server?
- [ ] Does `rsync client -> rsync server` transfers data securley like in `--rsh=ssh`?