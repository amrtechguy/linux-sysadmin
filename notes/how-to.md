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

- [ ] Projectx.script

```bash
#!/bin/bash

# create project dir
sudo mkdir ./projectx

# create subdir
sudo mkdir ./projectx/config
sudo chmod a=rwx ./projectx/config

# create subdir's files
sudo touch ./projectx/config/app.conf
sudo chmod ug=rw,o=r ./projectx/config/app.conf
sudo touch ./projectx/config/db.conf
sudo chmod a=rw ./projectx/config/db.conf
sudo touch ./projectx/config/secrets.key
sudo chmod u=rw,go=r ./projectx/config/secrets.key

# create subdir
sudo mkdir ./projectx/shared
sudo chmod a=rwx ./projectx/shared

# create subdir's files
sudo touch ./projectx/shared/notes.txt
sudo chmod a=rw ./projectx/shared/notes.txt
sudo touch ./projectx/shared/design.docx
sudo chmod u=rw,go=r ./projectx/shared/design.docx

# create subdir
sudo mkdir ./projectx/tmp
sudo chmod a=rwx ./projectx/tmp

# create subdir's files
sudo touch ./projectx/tmp/user1.tmp
sudo chmod a=rw ./projectx/tmp/user1.tmp
sudo touch ./projectx/tmp/user2.tmp
sudo chmod a=rw ./projectx/tmp/user2.tmp

# create subdir
sudo mkdir ./projectx/tools
sudo chmod u=rwx,go=rx ./projectx/tools

# create subdir's files
sudo touch ./projectx/tools/deploy.sh
sudo chmod u=rwx,go=rx ./projectx/tools/deploy.sh

# create subdir
sudo mkdir ./projectx/data
sudo chmod a=rwx ./projectx/data

# create subdir's files
sudo touch ./projectx/data/input.csv
sudo chmod ug=rw,o=r ./projectx/data/input.csv
sudo touch ./projectx/data/results.log
sudo chmod u=rw,go=r ./projectx/data/results.log
```
