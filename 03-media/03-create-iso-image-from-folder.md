# Howto

## File system operations

### Create ISO image from folder

The following command will crate the image file `image.iso` from the contents of folder `/home/fred/project`.  The image file will be labeled using the volume descriptor `Volume`.

```bash
$ genisoimage -r -input-charset iso8859-1 -V 'Volume' -o image.iso /home/fred/project
```

---
[Return to Index](../README.md)
