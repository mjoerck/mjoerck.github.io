---
layout: post
title: HP Microserver FreeNAS
subtitle: With full guide!
image: /img/FreeNAS/freenas_logo.jpg
tags: [Smart Home, Automation, DIY, FreeNAS]
---

Welcome to my first post about running FreeNAS. For this post I will be using a HP Proliant Microserver gen 7 n36l. However, you can follow this guide on your own server/computer, it should be the same. Please note that this guide is aimed at Windows users. The HP Microserver is aimed at small businesses who needs a file server. I managed to find one for only 50$ or 350 dkk which is a fairly solid deal.

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

![Rufus](/img/FreeNAS/rufus.jpg)

### Downloading FreeNAS and creating a bootable disk
1. Start by downloading [FreeNAS at their website.](https://www.freenas.org/download-freenas-release/)
2. Insert your USB drive into your computer.
3. Download [Rufus](https://rufus.ie/) (a program which will allow you to create a bootable USB Drive).
4. Run Rufus, and select your USB drive.
5. Click the disk image next to create a bootable disk using.
6. Select the .iso file you downloaded from FreeNAS.
7. Press start.

When the process has finished you have created your bootable disk, and you can now proceed to the next section.

![FreeNAS installation](/img/FreeNAS/freenas-boot-menu.png)

### Installation of FreeNAS
The installation of the OS itself is fairly self-explanatory and easy; however, I will cover it just in case.
If you boot up the server after having inserted the USB drive you should be met by a boot screen that displays FreeNAS as an option. You should hit continue.

1. Select install.
2. Select the disk from which you want your server to run from.
3. Click OK.
4. Enter your desired password.
5. Click OK.
6. Choose between BIOS and UEFI mode, this depends on your motherboard.
7. Wait for the installation to complete.
8. Reboot the server.

Once the server has rebooted you should be greeted by a screen which displays the server IP-address. You should change this IP-address to a static one, this will make your life easier in the long run; however, this is completely optional.
To change your IP-address do the following.

1. Click 1 and enter.
2. Select your interface and enter.
3. Select no three times.
4. Select yes to configure IPv4.
5. Click enter.
6. Type in an IP-address of your liking.
7. Type in your netmask (most likely 2).
8. Select no to configure IPv6.

Once you have done this, you are now ready to configure FreeNAS. Head over to your computer, we will configure the NAS through the web-interface.

![FreeNAS UI](/img/FreeNAS/freenas-interface.jpg)

### Configuring FreeNAS
Before we get started with configuring FreeNAS itself please ensure that your drives are installed properly and that you have access to the web interface through the static IP-address you set before. The dashboard should look something like the image above. We will get started by setting up your user accounts.

In the interface do the following:

1. Head to the account page and the submenu 'Groups'.
2. Press ADD in the top right corner.
3. Leave the GID and enter a name of your liking (I suggest admin).
4. Permit sudo and save.
5. Go to the submenu 'Users' and add a new user.
6. Fill in the information, some info is not required.
7. Deselect 'new primary group' and select the admin group we just created in the list below.
8. Check all permissions in the square of boxes in the lower left and permit sudo.
9. If you are using a windows computer with a Microsoft account you may want to check the box that says 'Microsoft Account' as well.

After successfully setting up the user accounts we can now proceed to setup the actual storage pools. In the left menu select 'Storage' and navigate to the submenu 'Pools' it should look something like this:

[INSERT IMAGE HERE]

To add your drives do the following:

1. Click ADD.
2. Create a new pool.
3. Name it whatever you would like.
4. Under 'Available Disks' select the drives that you would like to add to the pool (it is not recommended to mix different drive sizes).
5. When you are happy with the configuration click create.

If you wish you can go ahead and create multiple pools now.

6. Head to the 'Sharing' menu and select the submenu 'Windows (SMB) Shares'.
7. Click ADD.
8. Click the folder icon and select your pool from the subfolders. It should insert a path that looks something like this

```
/mnt/yourpoolnamehere
```

9. Click SAVE.
10. Do enable the service.

The NAS server is almost ready to be accessed from your file explorer now, but there are still a few steps left.
