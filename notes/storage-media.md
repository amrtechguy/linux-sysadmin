# Storage Media

## Notes
- `printer buffer` technique.

## Title

```bash
# filesystem table
less /etc/fstab

# mounted filesystems
mount

# unmount & mount
mkdir /mnt/cdrom
umount dev/sr1
mount -t iso9660 dev/sr1 /mnt/cdrom

# filesystems
df

# disk manipulation
fdisk /dev/sdb1

# create filesystem
mkfs -t vfat /dev/sdb1

# check filesystem
fsck /dev/sdb1

# read from device (5 blocks x 2048 bytes), write to stdout 
dd if=/dev/loop17 bs=2048 count=5

# Flash drive -> image
dd if=/dev/sdb1 of=flash.img

# Flash drive -> Flash drive
dd if=/dev/sdb1 of=/dev/sdc1

# CD-ROM -> iso image
dd if=/dev/sr1 of=ubuntu.iso

# Dir -> iso image
genisoimage -o cd.iso -R -J ./cd-files/

# mount iso image
mount -t iso9660 -o loop image.iso /mnt/cd/

# blanking (erasing) rewritable CD-ROM
wodim dev=/dev/cdrw blank=fast

# write image -> CD-ROM
wodim dev=/dev/cdrw image.iso

# file or filesystem status
stat image.iso

# integrity check
md5sum image.iso
mount -t iso9660 -o loop image.iso /mnt/cdrom
md5sum /mnt/cdrom/
```

## Gaps
- [ ] physical storage `hard disks` and `network storage` vs virtual storage devices `RAID (Redundant Array of Independent Disks)` and `LVM (Logical Volume Manager)`.
- [ ] `IDE` vs `SCSI` vs `SATA` vs `...`.
- [ ] Failed to unmount a flash drive `umount /dev/sdb1` → `umount: /media/user/ME: target is busy.`
    - Because it's being used by a user or process.
- [ ] Results of `mount` vs `df`.
- [ ] `primary` vs `extended` partitions.
- [ ] `fsck /dev/sdb1`: What is `Dirty bit`?
- [ ] `partition type` vs `filesystem type`.
- [ ] `partition UUID` vs `filesystem UUID`.
- [ ] What is the filesystem in specific and what are its components? 
- [ ] What is `Dirty bit`?

```bash
Dirty bit is set. Fs was not properly unmounted and some data may be corrupt.
1) Remove dirty bit
2) No action
[12?q]? 1
```

- [ ] `dd if=/dev/sdb1 of=flash.img`:
    - Does it copy all data blocks from the input device's file `/dev/sdb1` and write to the opposite sectors of the `output device` or `image` including the filesystem files?
- [ ] `CD-ROM` vs `DVD` media.
- [ ] `CD-ROM` vs `DVD` are they the devices or storage media?
- [ ] Can I use `dd` to burn like `wodim`?