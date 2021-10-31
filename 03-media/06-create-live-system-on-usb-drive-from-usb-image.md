# Howto

## File system operations

### Create Live system on USB drive from ISO image

The following command will record a live image `image.iso` to the device `/dev/sdc`.

```bash
$ dd if=image.iso of=/dev/sdc bs=8M
```

---
[Return to Index](../README.md)
