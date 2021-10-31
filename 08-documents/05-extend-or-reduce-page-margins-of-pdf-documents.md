# Howto

## PDF document editing

### Extend or reduce page margins of PDF documents

The following command crops or extends the margins of the file `infile.pdf` and writes the result to the file `outfile.pdf`. Replace the placeholders with negative values to crop the corresponding margin. Use positive values to extend the corresponding margin.

```bash
$ pdfcrop --clip --margins 'left top right bottom' infile.pdf outfile.pdf
```

---
[Return to Index](../README.md)
