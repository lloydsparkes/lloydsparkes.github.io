---
id: 327
title: 'The Home Server Part 2: Ubuntu &#038; ZFS'
date: 2014-02-23T10:38:46+00:00
author: Lloyd Sparkes
layout: post
guid: http://blog.lloydsparkes.co.uk/?p=327
permalink: /2014/02/the-home-server-part-2-ubuntu-zfs/
categories:
  - Random Notes
---
So I have my HP Micro Server. It has a modded BIOS. I have installed a spare SSD that I had into the OOD slot. Next step is Ubuntu.

Unfortunately I found the Ubuntu Server 13.10 doesn&#8217;t like to work with either of my USB keyboards which makes installing it impossible. So I got a Ubuntu 13.04 ISO and installed it via USB stick to the SSD, then upgraded to 13.10.

Now for ZFS I did the following

> <div>
>   sudo -i
> </div>
> 
> <div id="crayon-5309a80a2af3a447765111-2">
>   apt-get install python-software-properties software-properties-common
> </div>
> 
> <div>
>   add-apt-repository ppa:zfs-native/stable
> </div>
> 
> <div>
>   apt-get update
> </div>
> 
> <div>
>   apt-get install ubuntu-zfs
> </div>
> 
> <div>
>   apt-get install zfs-initramfs
> </div>

<div>
</div>

<div>
  I then put in my 3 500gb test HDD&#8217;s that I am going to use as practice for setting up and recovering zfs.
</div>

<div>
</div>

<div>
  Next I edited /etc/default/zfs to enable automatic mounting/umounting of zfs shares on startup and shutdown, as well as the zfs sharing properties. (Change the top 4 options in the file from no to yes)
</div>

<div>
</div>

<div>
  Execute the following to get the disk id&#8217;s of the disks  you want to use in your zfs pool:
</div>

<div>
</div>

> <div>
>   ls -l /dev/disk/by_id
> </div>

<div>
</div>

<div>
  Mine were:
</div>

<div>
</div>

> <div>
>   ata-WDC_WD5000AAKS-00TMA0_WD-WCAPW1902486<br /> ata-WDC_WD5000AAKS-00TMA0_WD-WCAPW1908191<br /> ata-SAMSUNG_HD501LJ_S0MUJ13P651726
> </div>

<div>
</div>

<div>
  Then to create my RAIDZ pool (the Zfs equivalent of raid5) with my 3x500GB disks:
</div>

<div>
</div>

> <div>
>   zpool create -f storage raidz /dev/disk/by-id/ata-WDC_WD5000AAKS-00TMA0_WD-WCAPW1902486 /dev/disk/by-id/ata-WDC_WD5000AAKS-00TMA0_WD-WCAPW1908191 /dev/disk/by-id/ata-SAMSUNG_HD501LJ_S0MUJ13P651726
> </div>

<div>
</div>

<div>
  Then to check its all created
</div>

<div>
</div>

> <div>
>   $> zpool list<br /> NAME      SIZE  ALLOC   FREE    CAP  DEDUP  HEALTH  ALTROOT<br /> storage  1.36T   220K  1.36T     0%  1.00x  ONLINE  &#8211;
> </div>
> 
> <div>
>
> </div>
> 
> <div>
>   $> zpool status
> </div>

<div>
</div>

<div>
  Now when I ran both of those command the size it gives you is the raw size of the pool which in this case is 1.36TB.
</div>

<div>
</div>

<div>
  Note also DEDUP is on. When I properly set this up with the final drives I plan to use I will be turning it off on some of my sub file systems.
</div>

<div>
</div>

<div>
  If I run the following:
</div>

<div>
</div>

> <div>
>   $> zfs list
> </div>
> 
> <div>
>   NAME      USED  AVAIL  REFER  MOUNTPOINT<br /> storage   137K   913G  38.6K  /storage
> </div>

<div>
</div>

<div>
  I only see 913GB because of the 1/3 of the data taken to use as a parity.
</div>

<div>
</div>

<div>
  Finally I am going to create a single zfs filesystem within my zfs filesystem
</div>

<div>
</div>

> <div>
>   $> zfs create storage/test
> </div>
> 
> <div>
>   $> zfs list
> </div>
> 
> <div>
>   NAME           USED  AVAIL  REFER  MOUNTPOINT<br /> storage        188K   913G  40.0K  /storage<br /> storage/test  38.6K   913G  38.6K  /storage/test
> </div>

<div>
</div>

<div>
  Next. Creating some data, losing a drive, and rebuilding
</div>