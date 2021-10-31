# Howto

## PDF document editing

### Reduce the size of scanned PDF documents

The following command will reduce the size of a scanned PDF document `infile` to screen-view-only quality and write the result to the file `outfile`.

```bash
$ ps2pdf14 -dPDFSETTINGS=/screen infile outfile
```

Available profiles are as follows:

- `screen` = Screen-view-only quality, 72 dots per inch
- `ebook` = Low quality, 150 dots per inch
- `printer` = High quality, 300 dots per inch
- `prepress` = High quality, color preserving, 300 dots per inch
- `default` = almost identical to `screen`

---
[Return to Index](../README.md)
