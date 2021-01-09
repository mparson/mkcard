# mkcard

A script for creating "sdcard" image files with an MBR patitioni table and a single FAT32 filesystem suitable for use with the (Commander X-16)[https://www.commanderx16.com] emulator.  When used in conjunction with the (mtools)[https://www.gnu.org/software/mtools/], and a suitable `~/.mtoolsrc` file, you can create images and copy files to & from the card image(s), from the command line, without needing any root permissions.

To create a 64 meg image file:

```
$ mkcard -s 64 -f card64.img
Checking that no-one is using this disk right now ... OK

Disk card64.img: 66 MiB, 69206016 bytes, 135168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

>>> Created a new DOS disklabel with disk identifier 0x3daf5bbc.
card64.img1: Created a new partition 1 of type 'W95 FAT32 (LBA)' and of size 65 MiB.
card64.img2: Done.

New situation:
Disklabel type: dos
Disk identifier: 0x3daf5bbc

Device      Boot Start    End Sectors Size Id Type
card64.img1       2048 135167  133120  65M  c W95 FAT32 (LBA)

The partition table has been altered.
Syncing disks.
```

And your `~/.mtoolsrc` could look something like:

```
mtools_skip_check=1 
drive x: file="~/card64.img"    exclusive partition=1
```

Now you can put files onto the card with:

```
$ mcopy /path/to/some/file.prg x:FILE.PRG
```

Using UPPERCASE filenames on the destination ensures that they show up properly in the emulator.
