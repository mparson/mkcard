# mkcard

```
./mkcard [-f filename] [-s size-in-megabytes]

To create a 64 MB file:

./mkcard -f card.img -s 64 

Due to limitations of the FAT32 filesystem type, the minimum size
is 32 MB.

If you run it w/o a '-s' flag, it will default to a 32 MB file.
```
