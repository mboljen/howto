# Howto

## Search operations

### Find all files containing a specific text recursively

The following command will search recursively for all files containing the phrase `password` in and below the directory `/home/fred`. The option `-i` enables case-insensitive pattern matching.

```bash
$ grep -r -i 'password' /home/fred
```

---
[Return to Index](../README.md)
