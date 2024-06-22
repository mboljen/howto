# Howto

## Video editing

### Scale existing video maintaining the given aspect ratio

The following command will scale the file `infile` to a width of 640 pixels and a height of 480 Pixels ignoring any aspect ratio.

```console
$ ffmpeg -i infile -vf 'scale=640:480' outfile
```

To maintain the given aspect ratio replace the secondary dimension with the parameter `-1`. In order to scale the video to a height of 480 Pixels, use the following command:

````console
$ ffmpeg -i infile -vf 'scale=-1:480' outfile
````

---
[Return to Index](../README.md)
