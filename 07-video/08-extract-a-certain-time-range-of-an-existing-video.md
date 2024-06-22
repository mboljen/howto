# Howto

## Video editing

### Extract a certain time range of an existing video

The following command will extract a video clip of length `1:00` from the video `infile` starting at position `10:23` and write the result to `output`.

```console
$ ffmpeg -i infile -ss '10:23' -t '1:00' -c copy outfile
```

---
[Return to Index](../README.md)
