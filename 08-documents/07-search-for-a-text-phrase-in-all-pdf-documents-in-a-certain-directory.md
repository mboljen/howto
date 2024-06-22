# Howto

## PDF document editing

### Search for a text phrase in all PDF files of a certain directory

The following command will look for the phrase `password` in all PDF documents in the folder `/home/fred`

```console
$ pdfgrep -H 'password' /home/fred
```

The search can be tuned using the following options:

- `-R`, `--recursive` = Include all subdirectories
- `-H`, `--with-filename` = Print all filenames with matches
- `-i`, `--ignore-case` = Case-insensitive pattern matching

---
[Return to Index](../README.md)
