# Howto

## User administration

### Change the UID of an existing user and the GID of an existing group

The following commands will change the user ID and group ID of user `fred` and group `dudes` from `1001` to `1058` respectively.

```bash
$ usermod -u 1058 fred
$ groupmod -g 1058 dudes
```

Afterwards, all files referring to the old user ID and group ID need to be updated recursively.

```bash
$ find / -user 1001 -exec chown -h 1058 {} \;
$ find / -group 1001 -exec chgrp -h 1058 {} \;
```

---
[Return to Index](../README.md)
