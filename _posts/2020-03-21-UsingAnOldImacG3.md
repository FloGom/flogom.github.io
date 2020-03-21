---
layout: post
title: "Using an old iMac G3 for video purpose"
categories:
  - Old Computer
tags:
  - imac G3
  - ubuntu
  - mac os x
  - tiger
  - video
---

## The beast...
Today the star of this post is a glorious iMac G3 DV Blueberry! This is the 400MHz CPU version, with a DVD player.

![imac G3 photo](2020-03-21-img\imac_blueberry.jpg)    
*Image from [www.vectronicsappleworlds.com](http://www.vectronicsappleworld.com/archives/vintage/0003.php)*

The system installed is Mac OS 10.2.8 a.k.a Jaguar.

## DVD playback
With DV iMac, DVD playback comes straight out of the box. The Apple installed software works great.

Only concern might be the slot loading DVD reader. It's known that with age this reader tends to keep the disc inserted... paper clip always does the trick to eject manually the disc.

## Hard drive capacity limit
If one wants to listen music, or watch video, the original hard drive might be too small: 10 GB full at 90% is not very useful.

Upgrading to bigger hard drive is not easy on these machines. Indeed the hard drive is difficult to reach as shown in [this iFixit tutorial](https://fr.ifixit.com/Tutoriel/iMac+G3+Model+M4984+Hard+Drive+Replacement/1563?lang=en)

In addition the interface used to connect the hard drive is IDE with an [IDC 40 pins connector](https://old.pinouts.ru/HD/IDE_pinout.shtml). This kind of Hard Drive are not easy to find, see [here](https://www.usedmac.com/index.php?_route_=mac-hard-drive/mac-ide-ata-hard-drive) for second-hand.

Of course adaptators exist, for example IDE to Sata (like below) to play with a SSD for example,
or IDE to Compact Flash.

![adaptator photo](2020-03-21-img\ide2sata.jpg)

Since there are 2 FireWire400 connectors available on this G3, it's possible to hook up an external hard drive. But on these machines there is no *Large Drive Support* (as mentionned in [Mactracker](http://mactracker.ca/index.html)) it means that only a maximum of 128 GB per drive is possible. Due to this limitation larger hard drives have to be partitionned in chunk of less than 128 GB.

Lubuntu was of great help to partition a 160 GB hard drive in 120 GB and 40 GB, indeed Windows 10 has dropped support of FAT32 in the *Disk* tool.

The two partitions appeared on the iMac's desktop. **So it's possible to divide a big hard drive in smaller pieces and still using the whole capacity.**

## Quicktime playback of MP4
As explained on the [Wikipedia page of Quicktime](https://en.wikipedia.org/wiki/QuickTime#QuickTime_and_MPEG-4), Quicktime 6 support only partially the MPEG-4 format using only Simple Profile. H264 encoding and decoding comes later with Quicktime 7 and it was shipped with Mac OS 10.4 Tiger.

To test video-playback on such a low end computer (comparing to today Smartphones) the system must be first upgraded to Mac OS 10.4.

