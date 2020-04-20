---
title: "Recover Root Password RHEL/CentOS 7"
date: "2017-02-05"
categories: linux
---

1. Boot up server
2. At boot menu, press any key to stop auto selection at grub menu
3. Highlight the kernel you wish to boot to and press `e`
4. Move cursor to linux16 line and hit `end` key on keyboard to go to the end of the line
5. Append rd.break to the end of the line
6. `Ctrl + x` - to boot with your modifications

The system will enter emergency mode with /sysroot directory mounted as read only. The sysroot directory is the root of your system drive.

1. `mount -o remount,rw /sysroot` - to remount the root as rw
2. `chroot /sysroot` - to chroot jail sysroot as the root file system
3. `passwd root` - to reset root password
4. `touch /.autorelabel` - this ensures that SELinux will add a label to any unlabeled files - This allows the password to be updated
5. `exit` - exit chroot jail
6. `exit` - exit debug shell
