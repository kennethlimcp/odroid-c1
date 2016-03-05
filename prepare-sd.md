### Steps to setup the microSD card (Mac OSx)

- Download the ubuntu/lubuntu image from the Odroid wiki: [Ubuntu 14.04](http://odroid.com/dokuwiki/doku.php?id=en:c1_release_linux_ubuntu)

- Run the command to decompress the image : `unxz xxxxx.xz`

- Format the SD card to clean it up. [SDformatter](https://www.sdcard.org/downloads/formatter_4) works great!

- Look at all the disk drive available: `sudo diskutil list`

```sh
/dev/disk2
   #:                       TYPE NAME                    SIZE       IDENTIFIER
   0:     FDisk_partition_scheme                        *15.9 GB    disk2
   1:             Windows_FAT_32 BOOT                    15.9 GB    disk2s1
```

- We will unmount the disk before performing the write:

```sh
sudo diskutil unmountDisk /dev/disk2
```

Output message: `Unmount of all volumes on disk2 was successful`

- Now it's time to burn to the SD!

```sh
sudo dd if=<my/odroid/image.img> of=</dev/path/of/card> bs=1m
```

If you add a `r` before the disk name, you will achieve faster write speed through "raw" mode

eg.

```sh
sudo dd if=c1-ubuntu-20150401.img of=/dev/rdisk2 bs=1m
```

**NOTE:** Be sure of the disk you are entering or you may risk corrupting your hard drive or other storage devices!

- You will see this once the write is completed:

```sh
4689+0 records in
4689+0 records out
4916772864 bytes transferred in 273.859123 secs (17953657 bytes/sec)
```

- Look into the SD card drive with name "boot" and open the `boot.ini` file


We will make some modifications to save ram by running headless!

- Here are the settings to change:

  - HDMI (setenv vpu "0")
  - VPU  (setenv hdmioutput "0")

Power up and get running!
