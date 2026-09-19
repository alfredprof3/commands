# Mount, Eject & Umount USB Drives in Linux

Mount
-----

exFAT File System
-----

⚠ exfat file system doesn't allow read/write permissions, alternatively use the following method.

**Install exFAT support packages**

`sudo apt install exfatprogs exfat-fuse -y`

**Mounting exFAT**

Permission denied" When Accessing Files.
Error: You can mount the drive but can’t read/write files (e.g., ls: cannot open directory '/mnt/exfat-drive': Permission denied).

Fix: By default, mount assigns ownership to root. To grant access to your user, add the uid and gid options in the mount command or /etc/fstab:

    Temporarily:

 →  `sudo mount -t exfat -o uid=1000,gid=1000 /dev/sdb1 /mnt/exfat-drive`

    (Replace 1000 with your user’s UID/GID; find them with id $USER.)


Other file systems
-----

Mounting an external drive.

`sudo mount /dev/sda1 /mnt/sdcard`


Umount
-----

First identify the device name of your USB drive by running the `lsblk` command, which will list all block devices attached/connected to your system.

→ `lsblk`

Look for your USB drive in the list which is usually labeled as `/dev/sdX` (e.g., `/dev/sda` `/dev/sdb` `/dev/sdc`). Unmount the USB drive by running the `umount` command.

→ `sudo umount /dev/sda`

Be sure the USB drive was successfully removed.

→ `lsblk`

Safely remove the USB drive from your computer.

→ `sudo eject /dev/sda`

Alternatively you can use `udisks2` tool to unmount and eject the USB drive.

```bash
sudo udisksctl unmount -b /dev/sda
sudo udisksctl power-off -b /dev/sda
```


References
-----

1. [How to Eject a USB Drive](https://linuxvox.com/blog/linux-how-to-eject-usb-drive/)
2. [Eject Command Linux with Examples](https://www.geeksforgeeks.org/linux-unix/eject-command-in-linux-with-examples/)
3. [How to Mount an exFAT Drive on Debian Linux](https://linuxvox.com/blog/how-to-mount-an-exfat-drive-on-debian-linux/)
