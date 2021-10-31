# Howto

## Photo editing

### Convert photos to PNG format

The following command will convert all JPEG files in the current working directory to PNG files.

```bash
$ mogrify -format png *.jpg
```

More options:

- The option `-crop 800x600+100+50 +repage` will crop an area of 800 pixels of width and 600 pixels of height located at a horizontal offset of 100 pixels from the left margin and a vertical offset of 50 pixels from the bottom margin.
- The option `-resize 800x600` will resize the image to a width of 800 pixels and a height of 600 pixels.


---
[Return to Index](../README.md)
