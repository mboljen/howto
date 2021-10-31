# Howto

## Video editing

### Increase or decrease the speed of a video

In order to increase the playback speed of the video `infile` reduce the presentation time-stamp parameter.

```bash
$ ffmpeg -i infile -vf "setpts=0.5*PTS" outfile
```

In order to decrease the playback speed of the video `infile` increase the presentation time-stamp parameter.

````bash
$ ffmpeg -i infile -vf "setpts=2.0*PTS" outfile
````

---
[Return to Index](../README.md)
