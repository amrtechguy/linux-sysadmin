# Secure and Standardize Projectx Directory for Development Team

## Scenario
The `/srv/projectx/` directory was provisioned by the sysadmin for a new development initiative.
Currently, all files and subdirectories are owned by `root:root` and permissions were left wide open during the initial setup.

Before handing it over to the `devteam`, you are tasked with securing the directory, normalizing ownership, and preparing it for safe collaboration.

### Initial State (Before Changes)

```bash
/srv/projectx/
├── config/             (owner: root:root, perms: drwxrwxrwx)
│   ├── app.conf        (owner: root:root, perms: -rw-rw-r--)
│   ├── db.conf         (owner: root:root, perms: -rw-rw-rw-)
│   └── secrets.key     (owner: root:root, perms: -rw-r--r--)
├── shared/             (owner: root:root, perms: drwxrwxrwx)
│   ├── notes.txt       (owner: root:root, perms: -rw-rw-rw-)
│   └── design.docx     (owner: root:root, perms: -rw-r--r--)
├── tmp/                (owner: root:root, perms: drwxrwxrwx)
│   ├── user1.tmp       (owner: root:root, perms: -rw-rw-rw-)
│   └── user2.tmp       (owner: root:root, perms: -rw-rw-rw-)
├── tools/              (owner: root:root, perms: drwxr-xr-x)
│   └── deploy.sh       (owner: root:root, perms: -rwxr-xr-x)
└── data/               (owner: root:root, perms: drwxrwxrwx)
    ├── input.csv       (owner: root:root, perms: -rw-rw-r--)
    └── results.log     (owner: root:root, perms: -rw-r--r--)
```

### projectx.sh
You can use this script to create the project with all sub dirs and files with the same structure and permissions mentioned above.

The script creates the `projectx` in the same dir, so you need to run it inside the dir `/srv/` or any other dir you prefer.

```bash
#!/bin/bash

# remove the project dir if exists
sudo rm -rf ./projectx 

# create the project dir
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

## Tasks

### 1. Audit Permissions
- [x] Generate a structured report of all files and directories with:
        - Path, owner, group, permissions.

```bash
find . -exec ls -ldh {} \; | sudo tee report.txt
```
        
- [ ] Identify security risks such as world-writable files.

```bash
???
```

### 2. Standardize Ownership
- [x] Assign ownership of all files and directories to:
        - User: `alice`
        - Group: `devteam`

```bash
# create alice's account
sudo useradd -m -c 'Alice' -s /bin/bash alice

# create devteam group
sudo groupadd devteam

# change ownership recursively
sudo chown -R alice:devteam .
```

### 3. Secure Configuration Files
- [x] Restrict access to `app.conf`, `db.conf`, and `secrets.key`:
        - Only `alice` should have read/write permissions.
        - No other users should access these files.

    ```bash
    sudo chmod u=rw,go= ./config/*
    ```

### 4. Enable Group Collaboration in Shared
- `/srv/projectx/shared/` must support collaboration:
    - [x] All `devteam` members can read/write.

    ```bash
    sudo chmod g=rw shared/*
    ```

    - [x] Group ownership should persist for new files.

    ```bash
    sudo chmod g+s shared/
    ```

    - [x] Other users can only read.

    ```bash
    sudo chmod o-w shared/
    ```

    - [ ] Users cannot delete or overwrite files created by others.

    ```bash
    ???
    ```

### 5. Secure Temporary Area
- `/srv/projectx/tmp/` should function as a safe temp space:
    - [x] All users can create files.
    - [ ] No user can delete or overwrite another user’s files.

    ```bash
    ???
    ```

### 6. Deploy Script Privileges
- `/srv/projectx/tools/deploy.sh`:
    - [ ] Should run with root privileges, even if executed by non-root users.

    ```bash
    ???
    ```

    - [ ] Must remain executable for the intended team.

    ```bash
    ???
    ```