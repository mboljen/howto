# Howto

## File system operations

### Mount ISO image

The following command will mount the image `image.iso` to the mount point `/media/iso`.  You probably need root privileges to invoke `mount`.

```console
$ mount -t iso9660 -o ro,loop image.iso /media/iso
```

---
[Return to Index](../README.md)
