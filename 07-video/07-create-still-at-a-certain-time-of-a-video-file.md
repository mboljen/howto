# Howto

## Video editing

### Create still at a certain time of a video file

The following command will capture an image at the position `10:23` of the video `infile` and write the result to the JPEG file `output`.

```bash
$ ffmpeg -i infile -ss '10:23' -t 1 -f mjpeg output
```

---
[Return to Index](../README.md)
