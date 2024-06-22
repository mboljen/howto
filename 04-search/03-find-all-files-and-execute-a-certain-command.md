# Howto

## Search operations

### Find all files and execute a certain command

The following command will find all files in and below the directory `/home/fred` and invoke the command `du -h` on each file.

```console
$ find /home/fred -type f -exec du -h {} \;
```

---
[Return to Index](../README.md)
