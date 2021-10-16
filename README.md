# Hint-book

[TOC]



## User administration



### Add an existing user to an existing group

The following command will add the user `fred` to the existing group `dudes`.

```bash
$ usermod -a -G dudes fred
```



### Assign another primary group to an existing user

This command will make the group `dudes` the primary group of user `fred`.

```bash
$ usermod -g dudes fred
```



### Terminate all processes of a normal user

The following command will terminate all processes of user `fred`. Do not apply this command to kill all processes of the root user.

```bash
$ pkill -KILL -u fred
```



### Change the UID of an existing user and the GID of an existing group

The following commands will change the user ID and group ID of user `fred` and group `dudes` from `1001` to `1058` respectively.

```bash
$ usermod -u 1058 fred
$ groupmod -g 1058 dudes
```

Afterwards, all files referring to the old user ID and group ID need to be updated recursively.

```bash
$ find / -user 1001 -exec chown -h 1058 {} \;
$ find / -group 1001 -exec chgrp -h 1058 {} \;
```



### List all members of a Kerberos group

The following commands will list all members of the Kerberos group `dudes`.

```bash
$ kinit
$ ipa group-show dudes
```



### Reset ACL permissions of an existing file structure

The following commands will remove all existing ACL permissions from folder `/mnt/share/fred` and will change file permissions to user `fred` and group `dudes`. The ACL permissions will then be set to `rwX` for the users `fred` and `barney` and to `rX` for the group `flintstones`. Other users are not allowed to access the files.

```bash
$ chown -R fred:dudes /mnt/share/fred
$ setfacl -R -b /mnt/share/fred
$ setfacl -R    -m u::rwX,u:barney:rwX,g:flintstones:rX,o::- /mnt/share/fred
$ setfacl -R -d -m u::rwX,u:barney:rwX,g:flintstones:rX,o::- /mnt/share/fred
```



## System administration



### Repair GRUB boot loader using Live USB Image

After booting from a Live system, the operating system on the remote device needs to be mounted to a folder of the Live system.  In the following, the remote system is located in the first partition of device `/dev/sda`.

```bash
$ mount /dev/sda1 /mnt
```

Bind the system folders and finally switch to the new environment by using the `chroot` command.

```bash
$ mount -o bind /dev /mnt/dev
$ mount -o bind /sys /mnt/sys
$ mount -t proc /proc /mnt/proc
$ cp /proc/mount /mnt/etc/mtab
$ chroot /mnt /bin/bash
```

Afterwards, the GRUB boot loader can be installed on the remote device.  When the installation has completed successfully, the user can return to the Live system.

```bash
$ grub-install /dev/sda
$ grub-install --recheck /dev/sda
$ update-grub
$ exit
```



### Upgrade a running Debian system from stable to testing

Make a backup of the current settings to avoid getting lost in a wrongly configured system. Note that upgrading to `testing` is not reversible, this means once upgraded it is impossible to downgrade to `stable` again.

```bash
$ cp /etc/apt/sources.list{,.bak}
```

Now apply the following changes to the configuration file `/etc/apt/sources.list` in order to switch from `stable` to `testing`.

```bash
$ sed -i -e 's/ \(stable|buster\)/ testing/ig' /etc/apt/sources.list
```

Update the package lists and download the new packages.

```bash
$ apt-get update
$ apt-get --download-only dist-upgrade
```

Finally, install all downloaded packages and update the distribution to `testing`.

```bash
$ apt-get dist-upgrade
```



### Find package in software repository providing a specific file

Use the following command to check which package of your software repository provides a specific file. After installation the database of the tool needs to be updated.

```bash
$ apt-file update
```

In this example, all packages providing the file `libexotic.so` will be detected:

```bash
$ apt-file search libexotic.so
```



## File system operations



### Change the label of a FAT file system

The following command will change the label of a FAT file system located on `/dev/sdc1` to `NEWLABEL`.

```bash
$ mlabel -i /dev/sdc1 -s  ::NEWLABEL
```



### Create an ISO image from an external media

The following command will create the image `image.iso` from the contents of device `/dev/cdrom`.

```bash
$ dd if=/dev/cdrom of=image.iso
```



### Create ISO image from folder

The following command will crate the image file `image.iso` from the contents of folder `/home/fred/project`.  The image file will be labeled using the volume descriptor `Volume`.

```bash
$ genisoimage -r -input-charset iso8859-1 -V 'Volume' -o image.iso /home/fred/project
```



### Mount ISO image

The following command will mount the image `image.iso` to the mount point `/media/iso`.  You probably need root privileges to invoke `mount`.

```bash
$ mount -t iso9660 -o ro,loop image.iso /media/iso
```



### Record CD or DVD from ISO image

The following command will record a CD on the device `/dev/cdrw` from the ISO image `image.iso`.

```bash
$ cdrecord -v -eject -tao dev=/dev/cdrw image.iso
```



### Create Live system on USB drive from ISO image

The following command will record a live image `image.iso` to the device `/dev/sdc`.

```bash
$ dd if=image.iso of=/dev/sdc bs=8M
```



### Erase a rewritable CD+RW disk

The following command will erase a rewritable CD+RW disk.

```bash
$ cdrecord dev=/dev/cdrw blank=all
```



### Format a rewritable DVD+RW disk

The following command will format a rewritable DVD+RW disk.

```bash
$ growisofs -Z /dev/dvdrw=/dev/zero
```



### Grep longest track on DVD disk

The following command will detect the longest track on a DVD disk.

```bash
$ lsdvd | grep Longest
```



### Copy complete track of a DVD disk to a file

The following command will copy track `2` of a DVD disk to the file `track2.vob`.

```bash
$ mplayer dvd://2 -v -dumpstream -dumpfile track2.vob
```





## Search operations



### Find all hard linked files in and below a directory

The following command will find all hard-linked files in the directory `/home/fred` sharing the same inode as file `test.txt`.

```bash
$ find /home/fred -samefile test.txt
```



### Remove all duplicate files in and below a directory with hard links

The following command will remove all duplicate files in and below the directory `/home/fred`  with hard links excluding zero-length files.

```bash
$ fdupes -rHn /home/fred
```



### Find all files and execute a certain command

The following command will find all files in and below the directory `/home/fred` and invoke the command `du -h` on each file.

```bash
$ find /home/fred -type f -exec du -h {} \;
```



### Change all file extensions to lowercase characters

The following command will convert the file extensions of all files in and below `/home/fred` into lowercase characters.

```bash
$ find /home/fred -type f -name '*.*' -exec sh -c 'a=$(echo "$0" | sed -r "s/([^.]*)\$/\L\1/") ; [ "$a" != "$0" ] && mv "$0" "$a" ' {} \;
```



### Find all files containing a specific text recursively

The following command will search recursively for all files containing the phrase `password` in and below the directory `/home/fred`. The option `-i` enables case-insensitive pattern matching.

```bash
$ grep -r -i 'password' /home/fred
```





## Audio file editing



### Convert MP3 file to ring tone for Apple iPhone

The following command will convert the MP3 file `input.mp3` to the file `output.m4r` which can be used as ring tone on Apple iPhones.

```bash
$ ffmpeg -i input.mp3 -ac 1 -b:a 128K -f mp4 -c:a aac output.m4r
```



### Add cover art to all MP3 files in the current folder

The following command will add the image file `cover.jpg` as cover art to all MP3 files in the current working directory.

```bash
$ eyeD3 --add-image=cover.jpg:FRONT_COVER *.mp3
```



## Photo editing



### Convert photos to PNG format

The following command will convert all JPEG files in the current working directory to PNG files.

```bash
$ mogrify -format png *.jpg
```

More options:

- The option `-crop 800x600+100+50 +repage` will crop an area of 800 pixels of width and 600 pixels of height located at a horizontal offset of 100 pixels from the left margin and a vertical offset of 50 pixels from the bottom margin.
- The option `-resize 800x600` will resize the image to a width of 800 pixels and a height of 600 pixels.



### Place logo in image file

The following command will insert `logofile`  at the X-position of 20 pixels and the Y-position of 10 pixels to `file`. The inserted picture will be scaled horizontally to 200 pixels and vertically to 100 pixels.

```bash
$ mogrify -draw 'image Over 20,10 200,100 "logofile"' file
```



### Place text in image files

The following command will insert the text `Copyright` at horizontal offset of 20 Pixels and vertical offset of 10 Pixels to the file `file`. The selected font family is Liberation at 12 points. The text color is white and the anchor point is centered.

```bash
$ mogrify -gravity center -font Liberation -fill white -pointsize 12 -draw "text 20,10 'Copyright'" file
```



### Add or modify the original date and time of a JPEG image

The following command will set the original time stamp of the JPEG image file `file` to `2020-Feb-17 08:20:00`.

```bash
$ exiftool "-DateTimeOriginal=2020:02:17 08:20:00" file
```



## Video editing



### Concatenate multiple MTS video files

The following command will concatenate the MTS files `infile1.mts` and `infile2.mts` and create the output file `outfile.mts`.

```bash
$ ffmpeg -i "concat:infile1.mts|infile2.mts" -c copy outfile.mts
```



### Convert Quicktime video to Matroska video

The following command will convert a Quicktime video `input.mov` to the Matroska video `output.mkv`.

```bash
$ ffmpeg -i infile.mov -c copy outfile.mkv
```



### Concatenate multiple Matroska videos

The following command will concatenate the Matroska files `infile1.mkv` and `infile2.mkv` and create the output file `outfile.mkv`.

```bash
$ mkvmerge -o outfile.mkv infile1.mkv + infile2.mkv
```



### Auto-detect black margins in a video

The following command will auto-detect a potentially black margin in the video file `videofile`. The output denotes the width, height and the horizontal and vertical offset in pixels and the format `width:height:xoff:yoff`.

```bash
$ ffplay -i videofile -vf "cropdetect=24:16:0"
```



### Crop video

The following command will crop an area of `width` and `height` at a horizontal offset `xoff` and a vertical offset of `yoff` from the input file `infile` and convert it to the file `outfile`.

```bash
$ ffmpeg -i infile -vf "crop=width:height:xoff:yoff" outfile
```



### Convert video including all video and audio tracks to MP4 format

The following command will convert all video and audio tracks of the input file `infile` to MP4 format and write the results to file `outfile`.

```bash
$ ffmpeg -i infile -map 0:v -map 0:a -c:v libx264 -crf 20 -vf yadif -c:a aac outfile
```



### Create still at a certain time of a video file

The following command will capture an image at the position `10:23` of the video `infile` and write the result to the JPEG file `output`. 

```bash
$ ffmpeg -i infile -ss '10:23' -t 1 -f mjpeg output
```



### Extract a certain time range of an existing video

The following command will extract a video clip of length `1:00` from the video `infile` starting at position `10:23` and write the result to `output`.

```bash
$ ffmpeg -i infile -ss '10:23' -t '1:00' -c copy outfile
```



### Scale existing video maintaining the given aspect ratio

The following command will scale the file `infile` to a width of 640 pixels and a height of 480 Pixels ignoring any aspect ratio.

```bash
$ ffmpeg -i infile -vf 'scale=640:480' outfile
```

To maintain the given aspect ratio replace the secondary dimension with the parameter `-1`. In order to scale the video to a height of 480 Pixels, use the following command:

````bash
$ ffmpeg -i infile -vf 'scale=-1:480' outfile
````



### Increase or decrease the speed of a video

In order to increase the playback speed of the video `infile` reduce the presentation time-stamp parameter. 

```bash
$ ffmpeg -i infile -vf "setpts=0.5*PTS" outfile
```

In order to decrease the playback speed of the video `infile` increase the presentation time-stamp parameter.

````bash
$ ffmpeg -i infile -vf "setpts=2.0*PTS" outfile
````



### Record screen sequence and save to video file

The following command will record a sequence of size `1920x1200` Pixels from the screen `:0.0`, scale the result to a size of `960x600`  Pixels and save the result to the file `outfile`.  

```bash
$ ffmpeg -f x11grab -s 1920x1200 -i :0.0 -s 960x600 -an outfile
```



### Convert multiple PNG images files to MP4 video

The following command will convert multiple image named by the pattern `img-%04d.png` starting at index number `12` to the output file `outfile` with a rate of `25` frames per second.

```bash
$ ffmpeg -framerate 25 -start_number 12 -i 'img-%04d.png' -c:v libx264 outfile
```



### Add a logo to a video file

The following command will scale the graphics file  `logofile` to a width of `300` Pixels maintaining the given aspect ratio and insert it at the lower left corner of the the video `infile` with a padding of `10` Pixels. The result is written to `outfile`. 

```bash
$ ffmpeg -i infile -qscale 0 -vf "movie=logofile,scale=300:-1 [watermark]; [in][watermark] overlay=10:main_h-overlay_h-10 [out]" outfile
```



### Create AVI video from PNG image files

The following command will use the tool `mencoder` to concatenate all PNG files of the current working directory at a frame rate of 25 fps and create the AVI file `outfile` with no sound.

```bash
$ mencoder mf://*.png -mf type=png:fps=25 -ovc copy -nosound -o outfile
```



### Convert video to a Windows Media Video

The following command will use the tool `mencoder` to convert the input video `infile` to a Windows Media Video and save the result to the file `outfile` with no sound.

```bash
$ mencoder infile -o outfile -ovc lavc -lavcopts vcodec=wmv2 -nosound
```



## PDF document editing



### Reduce the size of scanned PDF documents

The following command will reduce the size of a scanned PDF document `infile` to screen-view-only quality and write the result to the file `outfile`.

```bash
$ ps2pdf14 -dPDFSETTINGS=/screen infile outfile
```

Available profiles are as follows:

- `screen` = Screen-view-only quality, 72 dots per inch
- `ebook` = Low quality, 150 dots per inch
- `printer` = High quality, 300 dots per inch
- `prepress` = High quality, color preserving, 300 dots per inch
- `default` = almost identical to `screen`



### Extract single pages of a PDF document

The following command will extract the pages `3-4` and `6` from the file `infile.pdf` and write the result to the file `outfile.pdf`, 

```bash
$ pdftk infile.pdf cat 3-4,6 output outfile.pdf
```



### Concatenate multiple PDF document to a single PDF document

The following command will concatenate the files `infile1.pdf` and `infile2.pdf` and write the result to the file `outfile.pdf`.

```bash
$ pdftk infile1.pdf infile2.pdf cat output outfile.pdf
```



### Rotate a PDF document

The following command will rotate the file `infile.pdf` clockwise about 90 degrees and write the result to the file `outfile.pdf`.

```bash
$ pdftk infile.pdf cat E output outfile.pdf
```

Available options are as follows:

- `E` = Rotate clockwise about 90 degrees (east-side up)
- `S` = Rotate clockwise about 180 degrees (south-side up)
- `W` = Rotate clockwise about 270 degrees (west-side up)
- `N` = No rotation



### Extend or reduce page margins of PDF documents

The following command crops or extends the margins of the file `infile.pdf` and writes the result to the file `outfile.pdf`. Replace the placeholders with negative values to crop the corresponding margin. Use positive values to extend the corresponding margin.

```bash
$ pdfcrop --clip --margins 'left top right bottom' infile.pdf outfile.pdf
```



### Scale PDF document to DIN A5

The following command will scale the file `infile.pdf` to page format `a5paper` and write the result to the file `outfile.pdf`.

```bash
$ pdfjoin infile.pdf --paper a5paper --fitpaper false --outfile outfile.pdf
```



### Search for a text phrase in all PDF files of a certain directory

The following command will look for the phrase `password` in all PDF documents in the folder `/home/fred`

```bash
$ pdfgrep -H 'password' /home/fred
```

The search can be tuned using the following options:

- `-R`, `--recursive` = Include all subdirectories
- `-H`, `--with-filename` = Print all filenames with matches
- `-i`, `--ignore-case` = Case-insensitive pattern matching

