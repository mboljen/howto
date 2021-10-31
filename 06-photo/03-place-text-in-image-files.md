# Howto

## Photo editing

### Place text in image files

The following command will insert the text `Copyright` at horizontal offset of 20 Pixels and vertical offset of 10 Pixels to the file `file`. The selected font family is Liberation at 12 points. The text color is white and the anchor point is centered.

```bash
$ mogrify -gravity center -font Liberation -fill white -pointsize 12 -draw "text 20,10 'Copyright'" file
```

---
[Return to Index](../README.md)
