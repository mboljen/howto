# Howto

## System administration

### Find package in software repository providing a specific file

Use the following command to check which package of your software repository provides a specific file. After installation the database of the tool needs to be updated.

```console
$ apt-file update
```

In this example, all packages providing the file `libexotic.so` will be detected:

```console
$ apt-file search libexotic.so
```

---
[Return to Index](../README.md)
