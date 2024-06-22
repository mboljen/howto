# Howto

## Video editing

### Crop video

The following command will crop an area of `width` and `height` at a horizontal offset `xoff` and a vertical offset of `yoff` from the input file `infile` and convert it to the file `outfile`.

```console
$ ffmpeg -i infile -vf "crop=width:height:xoff:yoff" outfile
```

---
[Return to Index](../README.md)
