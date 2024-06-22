# Howto

## Photo editing

### Place logo in image file

The following command will insert `logofile`  at the X-position of 20 pixels and the Y-position of 10 pixels to `file`. The inserted picture will be scaled horizontally to 200 pixels and vertically to 100 pixels.

```console
$ mogrify -draw 'image Over 20,10 200,100 "logofile"' file
```

---
[Return to Index](../README.md)
