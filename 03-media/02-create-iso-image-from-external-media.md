# Howto

## File system operations

### Create an ISO image from an external media

The following command will create the image `image.iso` from the contents of device `/dev/cdrom`.

```bash
$ dd if=/dev/cdrom of=image.iso
```

---
[Return to Index](../README.md)
