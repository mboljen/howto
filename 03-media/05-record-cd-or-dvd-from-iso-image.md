# Howto

## File system operations

### Record CD or DVD from ISO image

The following command will record a CD on the device `/dev/cdrw` from the ISO image `image.iso`.

```console
$ cdrecord -v -eject -tao dev=/dev/cdrw image.iso
```

---
[Return to Index](../README.md)
