# Howto

## Video editing

### Concatenate multiple MTS video files

The following command will concatenate the MTS files `infile1.mts` and `infile2.mts` and create the output file `outfile.mts`.

```bash
$ ffmpeg -i "concat:infile1.mts|infile2.mts" -c copy outfile.mts
```

---
[Return to Index](../README.md)
