# Howto

## Search operations

### Change all file extensions to lowercase characters

The following command will convert the file extensions of all files in and below `/home/fred` into lowercase characters.

```bash
$ find /home/fred -type f -name '*.*' -exec sh -c 'a=$(echo "$0" | sed -r "s/([^.]*)\$/\L\1/") ; [ "$a" != "$0" ] && mv "$0" "$a" ' {} \;
```

---
[Return to Index](../README.md)
