# How To?

- [x] Extract a specific field of each line.

```bash
cut -d ':' -f 1 < /etc/passwd
cat /etc/passwd | cut -d ':' -f 1
```

- [x] List only files, dirs, or links.

```bash
find ~/data/*.bak -maxdepth 1 -type f
```

- [x] Using xargs to pass args.

```bash
find /etc/*disk* -maxdepth 1 -type f -print0 | xargs -0 ls -l
```

- [x] cleanup.sh

```bash
echo "[Task] Removing empty log files."
find /tmp/projectx/logs/ -type f -size 0c -exec rm {} \;

echo "[Task] Appending +1MB log files to an archive."
find /tmp/projectx/logs/ -type f -size +1M -exec tar -rf /tmp/projectx/backup_logs.tar {} \;
```