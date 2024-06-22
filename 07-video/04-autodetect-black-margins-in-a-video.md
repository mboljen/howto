# Howto

## Video editing

### Auto-detect black margins in a video

The following command will auto-detect a potentially black margin in the video file `videofile`. The output denotes the width, height and the horizontal and vertical offset in pixels and the format `width:height:xoff:yoff`.

```console
$ ffplay -i videofile -vf "cropdetect=24:16:0"
```

---
[Return to Index](../README.md)
