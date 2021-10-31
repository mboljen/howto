# Howto

## Video editing

### Convert video including all video and audio tracks to MP4 format

The following command will convert all video and audio tracks of the input file `infile` to MP4 format and write the results to file `outfile`.

```bash
$ ffmpeg -i infile -map 0:v -map 0:a -c:v libx264 -crf 20 -vf yadif -c:a aac outfile
```

---
[Return to Index](../README.md)
