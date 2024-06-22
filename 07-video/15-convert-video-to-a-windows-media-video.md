# Howto

## Video editing

### Convert video to a Windows Media Video

The following command will use the tool `mencoder` to convert the input video `infile` to a Windows Media Video and save the result to the file `outfile` with no sound.

```console
$ mencoder infile -o outfile -ovc lavc -lavcopts vcodec=wmv2 -nosound
```

---
[Return to Index](../README.md)
