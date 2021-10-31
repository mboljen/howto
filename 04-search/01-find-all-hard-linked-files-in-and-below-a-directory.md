# Howto

## Search operations

### Find all hard linked files in and below a directory

The following command will find all hard-linked files in the directory `/home/fred` sharing the same inode as file `test.txt`.

```bash
$ find /home/fred -samefile test.txt
```

---
[Return to Index](../README.md)
