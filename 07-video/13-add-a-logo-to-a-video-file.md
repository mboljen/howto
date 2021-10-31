# Howto

## Video editing

### Add a logo to a video file

The following command will scale the graphics file  `logofile` to a width of `300` Pixels maintaining the given aspect ratio and insert it at the lower left corner of the the video `infile` with a padding of `10` Pixels. The result is written to `outfile`.

```bash
$ ffmpeg -i infile -qscale 0 -vf "movie=logofile,scale=300:-1 [watermark]; [in][watermark] overlay=10:main_h-overlay_h-10 [out]" outfile
```

---
[Return to Index](../README.md)
