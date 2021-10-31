# Howto

## Video editing

### Create AVI video from PNG image files

The following command will use the tool `mencoder` to concatenate all PNG files of the current working directory at a frame rate of 25 fps and create the AVI file `outfile` with no sound.

```bash
$ mencoder mf://*.png -mf type=png:fps=25 -ovc copy -nosound -o outfile
```

---
[Return to Index](../README.md)
