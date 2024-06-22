# Howto

## Video editing

### Record screen sequence and save to video file

The following command will record a sequence of size `1920x1200` Pixels from the screen `:0.0`, scale the result to a size of `960x600`  Pixels and save the result to the file `outfile`.

```console
$ ffmpeg -f x11grab -s 1920x1200 -i :0.0 -s 960x600 -an outfile
```


---
[Return to Index](../README.md)
