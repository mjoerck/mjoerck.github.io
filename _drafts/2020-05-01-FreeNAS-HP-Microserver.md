---
layout: post
title: HP Microserver FreeNAS
subtitle: with full guide and explanation
image: /img/freenas_logo.jpg
tags: [Smart Home, Automation, DIY, FreeNAS]
---

Welcome to my first post about running FreeNAS. For this post I will be using a HP Proliant Microserver gen 7 n36l. However, you can follow this guide on your own server/computer, it should be the same. The HP Microserver is aimed at small businesses who needs a file server. I managed to find one for only 50$ or 350 dkk which is a fairly solid deal.

### Getting started
Before we get started with installing FreeNAS and setting it up, lets talk about specs. The specifications of your fileserver are actually not that important; however, I still have some recommendations for you.
For FreeNAS the following specs are generally considered the recommended minimum hardware:

- Multicore 64-bit processer (A dual core processer is more than enough for a fileserver)
- An operating system drive (16 GB or larger recommended, SATA DOM, M.2, or SSD recommended)
- 8 GB or more RAM (ECC recommended)
- At least two SATA disks
- NAS drives (I recommended the [WD Red](https://www.amazon.com/gp/product/B07PGWXQCM/ref=as_li_tl?ie=UTF8&tag=ixyt-20&camp=1789&creative=9325&linkCode=as2&creativeASIN=B07PGWXQCM&linkId=346f84e146aa179e59457d357552604b))
- An ethernet network port

I will not explain how to build or install the drives in this post; however, there are many profound guides on YouTube.

### Downloading FreeNAS and creating a bootable disk
1. Start by downloading [FreeNAS at their website.](https://www.freenas.org/download-freenas-release/)
2. Insert your USB drive into your computer.
3. Download [Rufus](https://rufus.ie/) (a program which will allow you to create a bootable USB Drive).
4. Run Rufus, and select your USB drive.
5. Click the disk image next to create a bootable disk using.
6. Select the .iso file you downloaded from FreeNAS.
7. Press start.

When the process has finished you have created your bootable disk, and you can now proceed to the next section.

### Installation of FreeNAS
The installation of the OS itself is fairly self-explanatory and easy; however, I will cover it just in case.
If you boot up the server after having inserted the USB drive you should be met by a boot screen that displays FreeNAS as an option. You should hit continue.

1. Select install.
2. Select the disk from which you want your server to run from.
3. Click OK.
4. Enter your desired password.
5. Click OK.
6. Wait for the installation to complete.
7. Reboot the server.

Once the server has rebooted you should be greeted by a screen which displays the server IP-address. You can change this into a static IP by following the menu system; however, this is completely optional - but it will make the following steps easier.

------------- OBS, skriv om, hvordan man gør dette. ----------------

### Configuring FreeNAS
