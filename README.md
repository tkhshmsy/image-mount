# image-mount
mount wrapper for multi-partitioned-disk-image

# How to use
this is the BASH script to mount the partition from multi-partitioned-disk-image file.

## format
```bash
Usage： image-mount.sh <imagefile> [<part-num> <mount-point>]
```

## dump the list of partitions

If the only argument is \<imagefile\>, the result of "fdisk -l \<imagefile\>" will be dumped.

```
$ ./image-mount.sh imagefile.img
imagefile.img1 *     16384  186775  170392 83.2M  c W95 FAT32 (LBA)
imagefile.img2      196608 7448431 7251824  3.5G 83 Linux
```

## mount the partition from imagefile

If you add \<part-num\> and \<mount-point\>, it will mount.

```
$ sudo ./image-mount.sh imagefile.img 2 ./mount/
imagefile.img1 *     16384  186775  170392 83.2M  c W95 FAT32 (LBA)
imagefile.img2      196608 7448431 7251824  3.5G 83 Linux
>> mount -o loop,offset=100663296 imagefile.img ./mount/

./mount/
合計 88
drwxr-xr-x 19 root     root      4096  3月  2 11:23 .
drwxrwxr-x  3 tkhshmsy tkhshmsy  4096  4月  7 16:57 ..
drwxr-xr-x  2 root     root      4096  3月  2 11:23 bin
drwxr-xr-x  2 root     root      4096  3月  2 11:22 boot
drwxr-xr-x  2 root     root      4096 11月  9 13:25 dev
drwxr-xr-x 41 root     root      4096  3月  2 11:23 etc
drwxr-xr-x  5 root     root      4096  3月  2 11:22 home
drwxr-xr-x 11 root     root      4096  3月  2 11:23 lib
drwx------  2 root     root     16384  3月  2 11:23 lost+found
drwxr-xr-x  2 root     root      4096 11月  9 13:25 media
drwxr-xr-x  9 root     root      4096  3月  2 11:22 mnt
drwxr-xr-x  8 root     root      4096  3月  2 11:22 opt
dr-xr-xr-x  2 root     root      4096 11月  9 13:25 proc
drwxr-xr-x  2 root     root      4096 11月  9 13:25 run
drwxr-xr-x  3 root     root      4096  3月  2 11:23 sbin
dr-xr-xr-x  2 root     root      4096 11月  9 13:25 sys
drwxrwxrwt  2 root     root      4096 11月  9 13:25 tmp
drwxr-xr-x 10 root     root      4096  3月  2 11:22 usr
drwxr-xr-x  9 root     root      4096  3月  2 11:23 var

partition 2 is mounted on ./mount/, remember umount when you're done to use.
```

# Depends
- bash
- fdisk
- mount

# Reference
- https://qiita.com/suzutsuki0220/items/38148dad5259a4dd9a6d
  - this article is written in Japanese

# License
- MIT

# Author
- tkhshmsy@gmail.com
