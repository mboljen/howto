# Howto

## PDF document editing

### Rotate a PDF document

The following command will rotate the file `infile.pdf` clockwise about 90 degrees and write the result to the file `outfile.pdf`.

```console
$ pdftk infile.pdf cat E output outfile.pdf
```

Available options are as follows:

- `E` = Rotate clockwise about 90 degrees (east-side up)
- `S` = Rotate clockwise about 180 degrees (south-side up)
- `W` = Rotate clockwise about 270 degrees (west-side up)
- `N` = No rotation

---
[Return to Index](../README.md)
