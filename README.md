# IsoBuster support for Clonezilla
This repository contains examples that show how [IsoBuster](https://www.isobuster.com) can open a subset of Clonezilla created image files

This is achieved by creating [*.imlst](https://github.com/Isobuster/imlst) files that reference the relevant Clonezilla created files

As of IsoBuster 5.5:

- IsoBuster supports random and virtualized file access inside \*.gz and \*.bz2 compressed image files

- IsoBuster supports detecting and parsing **PartClone** and **NTFSClone** Image files.

As such it is able to open various volumes / partitions that are created by CloneZilla

It is also able to show the entire disk image, by stitching all volumes / partitions together.<br>
All this is done via [*.imlst](https://github.com/Isobuster/imlst) magic.

Example:

```c++
\\#\img(,,-1)sdc-gpt-1st // -1 resolves into proper size based on the MBR and GPT data

\\#\img()<<sdc1.vfat-ptcl-img.gz.aa|sdc1.vfat-ptcl-img.gz.ab|sdc1.vfat-ptcl-img.gz.ac>>

\\#\img()<<sdc2.exfat-ptcl-img.gz.aa|sdc2.exfat-ptcl-img.gz.ab>>

\\#\img()<<sdc3.ntfs-ptcl-img.gz.aa|sdc3.ntfs-ptcl-img.gz.ab|sdc3.ntfs-ptcl-img.gz.ac|sdc3.ntfs-ptcl-img.gz.ad|sdc3.ntfs-ptcl-img.gz.ae|sdc3.ntfs-ptcl-img.gz.af|sdc3.ntfs-ptcl-img.gz.ag|sdc3.ntfs-ptcl-img.gz.ah>>

\\*\Filler up to backup -BUT EMPTY- GPT:245760:0x55

sdc-gpt-2nd
```

![test_5](/Screenshots/test_5.png)
