# Project 4 Part 2 - Adding a new file system type to Minix
- Brandon Tarney
- May 3 2017
- JHU EP CS 605.412
- Project 4 Part 2 - Adding a new file system type to Minix

## How to create a new filesystem type 
New file systems are created with the `mkfs` command meaning we will need a new implementation of this command. The file system is identical to v3 Minix filesystem, aside from the file system type which is embedded in the superblock of the file system when it is created. First we would need to update the makefile for the appropriate program (i.e. PROG= mkfs.mfshw4). Next we modify the magic # (essentially the file system type) contained in the super block which can be found in sbin.mkfs/v3/const.h (#define SUPER_V3 0x4d5a) as well as the macro SUPER_MAGIC which points to SUPER_V# (we simply point to our renamed SUPER_V3 which now has a new macro). This "magic number" is stored in Super.H struct super_block superblock.s_magic and is used to precalculate s_inodes_per_block. 


## How to create a disk with that new filesystem
"MKFS" is the standard unix utility which creates a file system on a fresh disk. It's typcially located on /sbin/. The exact use of this utility would look something like "mkfs.hw4 -t <type> <partition>" . We will use the type we just created and any partition available.

## How to create a new filesystem service associated with the new filesystem
I should probalby have mentioned by now we should rename all the #ifndef & @define statements which use "MFS" and replaced them with "fs_h4" or something like it. There are many constants and variables we should probably rename. We might reconsider some macro's as well, such as mfsdir.h MFS_DIRSIZ which controls the directory size (name) We would have to modify the makefile first and foremost to build our service (fs_hw4, instead of mfs). Once again we must modify const.h to include a macro defintion of our file system type and its associated magic number. We can also modify Super.c just to add the new file system to show our file system only supports our new file system type. 

## How to modify the 'mount' command to mount the new filesystem within the Minix file system hierarchy
