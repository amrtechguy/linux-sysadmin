# Provisioning and Securing Storage for Dev Team

## Scenario
A developer team requested a new storage location for project data. They need a dedicated mount point on `/mnt/projects` with enough space, correct permissions for their group, and persistence across reboots.

## Main Steps

### Identify and Prepare the New Disk
- [x] Check for available storage devices (e.g., `/dev/sdb`).

```bash
lsblk
```

- [x] Create a new partition on the disk.

```bash
sudo fdisk /dev/sdb
# Command (m for help):
n
# Partition type
#    p   primary (0 primary, 0 extended, 4 free)
#    e   extended (container for logical partitions)
# Select (default p):
p
# Partition number (1-4, default 1):
1
# First sector (2048-8388607, default 2048): 
<ENTER>
# Last sector, +/-sectors or +/-size{K,M,G,T,P} (2048-8388607, default 8388607):
<ENTER>
# Created a new partition 1 of type 'Linux' and of size 4 GiB.
# Partition #1 contains a ext4 signature.
# Do you want to remove the signature? [Y]es/[N]o:
y
# Command (m for help):
w
```

- [x] Format the partition with `ext4`.

```bash
sudo mkfs -t ext4 /dev/sdb1
sudo partprobe # update the kernel with new partition table changes
# check updates
lsblk --fs /dev/sdb
blkid -p /dev/sdb1 # `blkid` uses cache, need to use proping
```

### Create Mount Point and Mount the Filesystem
- [x] Create the directory `/mnt/projects`.

```bash
sudo mkdir /mnt/projects
```

- [x] Mount the new partition temporarily to `/mnt/projects`.

```bash
sudo mount /dev/sdb1 /mnt/projects/
```

- [x] Verify it is mounted correctly with the expected size.

```bash
lsblk --fs /dev/sdb
df -h /mnt/projects # checks the mount point
```

### Set Ownership and Permissions
- [x] Create a group `devteam` if it doesn’t exist.

```bash
sudo groupadd devteam
```

- [x] Ensure all developers (users: `alice`, `bob`, `carol`) are members of `devteam`.

```bash
sudo usermod -aG devteam alice
sudo usermod -aG devteam bob
sudo usermod -aG devteam carol
```

- [x] Set ownership of `/mnt/projects` to `root:devteam`.

```bash
sudo chown root:devteam /mnt/projects/
```

- [x] Apply permissions `rwxrws---` (2770) so group members can collaborate and new files inherit the group

```bash
sudo chmod u=rwx,g=rwxs,o= /mnt/projects/
```

### Make the Mount Persistent
- [x] Retrieve the filesystem UUID of the new partition.

```bash
sudo blkid -p /dev/sdb1
```

- [x] Add an entry to `/etc/fstab` to mount it automatically at boot:
    - Device: `UUID=<uuid>`
    - Mount point: `/mnt/projects`
    - Filesystem: `ext4`
    - Options: `defaults`
    - Permissions: `0 2`

```bash
# used `vi /etc/fstab` to add the line:
# UUID=dc3e3dce-c5ab-4cd1-8ea0-809db7109c53 /mnt/projects ext4 defaults 0 2
```

### Final Validation
- [x] Re-mount all filesystems to confirm fstab entry works.

```bash
sudo mount -a # reread `/etc/fstab`, check syntax
```

- [x] Verify that `/mnt/projects` is mounted with the correct UUID.

```bash
# UUID
sudo blkid -p /dev/sdb1
# Verify
lsblk --fs /dev/sdb1
```

- [x] Test that members of `devteam` can create and edit files, while others are denied.

```bash
cd /mnt/projects # access denied
sudo usermod -aG devteam me # add my account to the group `devteam` to test
sudo su - me # new login session, refresh my group mempership 
cd /mnt/projects
mkdir my_test
cd my_test
touch my_test.txt
echo "$(date)" > my_test.txt
cat my_test.txt
cd /mnt/projects
rm -rf my_test/
```

## Notes
- ...

## Gaps
- [ ] ...