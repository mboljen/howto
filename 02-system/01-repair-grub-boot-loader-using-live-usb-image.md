# Howto

## System administration

### Repair GRUB boot loader using Live USB Image

After booting from a Live system, the operating system on the remote device needs to be mounted to a folder of the Live system.  In the following, the remote system is located in the first partition of device `/dev/sda`.

```console
$ mount /dev/sda1 /mnt
```

Bind the system folders and finally switch to the new environment by using the `chroot` command.

```console
$ mount -o bind /dev /mnt/dev
$ mount -o bind /sys /mnt/sys
$ mount -t proc /proc /mnt/proc
$ cp /proc/mount /mnt/etc/mtab
$ chroot /mnt /bin/bash
```

Afterwards, the GRUB boot loader can be installed on the remote device.  When the installation has completed successfully, the user can return to the Live system.

```console
$ grub-install /dev/sda
$ grub-install --recheck /dev/sda
$ update-grub
$ exit
```

---
[Return to Index](../README.md)
