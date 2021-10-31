# Howto

## PDF document editing

### Extract single pages of a PDF document

The following command will extract the pages `3-4` and `6` from the file `infile.pdf` and write the result to the file `outfile.pdf`,

```bash
$ pdftk infile.pdf cat 3-4,6 output outfile.pdf
```

---
[Return to Index](../README.md)
