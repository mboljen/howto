# Howto

## Audio file editing

### Convert MP3 file to ring tone for Apple iPhone

The following command will convert the MP3 file `input.mp3` to the file `output.m4r` which can be used as ring tone on Apple iPhones.

```bash
$ ffmpeg -i input.mp3 -ac 1 -b:a 128K -f mp4 -c:a aac output.m4r
```

---
[Return to Index](../README.md)
