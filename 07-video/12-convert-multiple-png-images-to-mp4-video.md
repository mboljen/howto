# Howto

## Video editing

### Convert multiple PNG images to MP4 video

The following command will convert multiple image named by the pattern `img-%04d.png` starting at index number `12` to the output file `outfile` with a rate of `25` frames per second.

```console
$ ffmpeg -framerate 25 -start_number 12 -i 'img-%04d.png' -c:v libx264 outfile
```

---
[Return to Index](../README.md)
