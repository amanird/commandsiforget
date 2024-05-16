# commandsiforget

if i wanted to make sure that the filesystem supports the whole amount of storage (2tb in this instance) which filesystem should i use  if i want the ssd to be used or be able to be used across different os (linux, windows, mac)

if i have important school documents, projects, and old movies on my ssd and wanted this drive to be able to be plugged into any computer and have the content and data be easily accessable would you still recommend exfat or another filesystem

A: exFAT

TO FORMAT THE DRIVE:

The lsblk command provides information about all available block devices. You can use it with the -f option to display the filesystem type.
  lsblk -f

Unmount the SSD if it is already mounted.
  sudo umount /dev/sdX1

Format the SSD as exFAT.
  sudo mkfs.exfat /dev/sdX

Verify the new filesystem:
  lsblk -f
