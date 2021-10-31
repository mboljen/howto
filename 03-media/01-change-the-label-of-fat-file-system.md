# Howto

## File system operations

### Change the label of a FAT file system

The following command will change the label of a FAT file system located on `/dev/sdc1` to `NEWLABEL`.

```bash
$ mlabel -i /dev/sdc1 -s  ::NEWLABEL
```

---
[Return to Index](../README.md)
