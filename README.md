# commandsiforget

This README contains a list of commands I forget.

# Formatting a drive

#### You should unmount each partition individually, and then format the drive itself 
#### (ex: Partition: sda1, sda2. Drive: sda)

The lsblk command provides information about all available block devices. You can use it with the -f option to display Drives, Filesystem Types, Labels, UUID, Storage Available, Mountpoints:
```
lsblk -f
```

Unmount the SSD if it is already mounted:
```
sudo umount /dev/sdX1
```

Format the SSD as exFAT:
```
sudo mkfs.exfat /dev/sdX
```

Verify the new filesystem:
```
lsblk -f
```

# Rename removable device

#### If you format something and then the name is defaulted to something you don't like and it doesn't have a lable and the mount point is /run/media/user/[UUID]:

Verify the Label:
```
lsblk -f
```

Make sure  what you want to change is unmounted:
```
sudo umount /dev/sda1
```

Set the label for exFAT:
```
sudo exfatlabel /dev/sda1 YourLabel
```

Verify the Label:
```
lsblk -f
```

# Mount with the Label

#### To mount the partition with the new label, you can create a directory and manually mount it, or update your /etc/fstab to automate the process.

Manual Mount:
```
sudo mkdir /mnt/YourLabel
```

Mount the partition:
```
sudo mount /dev/sda1 /mnt/YourLabel
```

Automate Mounting with /etc/fstab:
```
sudo nano /etc/fstab
```

Add an entry for your partition:
```
LABEL=YourLabel /mnt/YourLabel exfat defaults 0 2
```

Test the new fstab entry:
```
sudo mount -a
```

Verify the mounting:
```
lsblk -f
```

# View hidden files within a directory

Home directory:

```
ls -a ~
```

Directory of [insert path]:
```
ls -a /path/to/thing
```






























