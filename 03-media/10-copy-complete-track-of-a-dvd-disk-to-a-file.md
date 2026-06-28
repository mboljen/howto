# Howto

## File system operations

### Copy complete track of a DVD disk to a file

The following command will copy track `2` of a DVD disk mount at `/dev/sr1` to the file `track2.vob`.

```console
$ mplayer dvd://2 -v -dvd-device=/dev/sr1 -dumpstream -dumpfile track2.vob
```

---
[Return to Index](../README.md)
