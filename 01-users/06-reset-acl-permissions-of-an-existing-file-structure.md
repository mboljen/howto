# Howto

## User administration

### Reset ACL permissions of an existing file structure

The following commands will remove all existing ACL permissions from folder `/mnt/share/fred` and will change file permissions to user `fred` and group `dudes`. The ACL permissions will then be set to `rwX` for the users `fred` and `barney` and to `rX` for the group `flintstones`. Other users are not allowed to access the files.

```bash
$ chown -R fred:dudes /mnt/share/fred
$ setfacl -R -b /mnt/share/fred
$ setfacl -R    -m u::rwX,u:barney:rwX,g:flintstones:rX,o::- /mnt/share/fred
$ setfacl -R -d -m u::rwX,u:barney:rwX,g:flintstones:rX,o::- /mnt/share/fred
```

---
[Return to Index](../README.md)
