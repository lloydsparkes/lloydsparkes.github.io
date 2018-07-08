---
id: 332
title: 'The Home Server Part 3: ZFS Recovery'
date: 2014-02-23T11:45:23+00:00
author: Lloyd Sparkes
layout: post
guid: http://blog.lloydsparkes.co.uk/?p=332
permalink: /2014/02/the-home-server-part-3-zfs-recovery/
categories:
  - Random Notes
---
To illustrate zfs recovery, and to check it works. I am going to:

  1. Create a number of files, of various sizes.
  2. Produce a strong hash of those files sha512
  3. Shutdown
  4. Remove a disk
  5. Put in a different disk, but of the same size
  6. Repair the pool with the new disk &#8211; somehow
  7. Validate that the files I created, match the recovered files by checking their hashes

Now this is only a basic test, and wont cover all scenarios. Its more about getting acquainted with zfs, checking it works as I hope (although the large body of users using it, hopefully means it does). And learning how to rebuild my pool in the case of a disk failure.

The latter is probably the most important part.

So lets create some files. I just ran the command below a number of times changing the output filename and count to change the size of the resulting file.

> dd if=/dev/urandom of=testfile1.a bs=1M count=1024

As a interesting note, I saw I was getting a consistent 10MB/s throughput with this which seems quite good.

Next I did

> ls -al > ~/test\_ls\_output.txt

To create a directory listing I can use later for comparison.

Then I generated the hashes:

> sha512sum testfile1.a > ~/testfile1.a-CHECKSUM

Then to validate the hash:

> sha512sum -c ~/testfile1.a-CHECKSUM

So that&#8217;s steps 1 and 2 done, now to shutdown and switch out the drives.

So having rebooted I ran:

> $> zpool status
> 
> pool: storage
> 
> state: DEGRADED
> 
> status: One or more devices could not be used because the label is missing or         invalid.  Sufficient replicas exist for the pool to continue         functioning in a degraded state. action: Replace the device using &#8216;zpool replace&#8217;.    see: <http://zfsonlinux.org/msg/ZFS-8000-4J>
> 
> scan: none requested config:
> 
> NAME                                           STATE     READ WRITE CKSUM
> 
> storage                                        DEGRADED     0     0     0
> 
> raidz1-0                                     DEGRADED     0     0     0
> 
> ata-WDC\_WD5000AAKS-00TMA0\_WD-WCAPW1902486  ONLINE       0     0    0
> 
> ata-WDC\_WD5000AAKS-00TMA0\_WD-WCAPW1908191  ONLINE       0     0     0
> 
> ata-SAMSUNG\_HD501LJ\_S0MUJ13P651726         UNAVAIL      0     0     0
> 
> errors: No known data errors

So we can see a disk is missing, and the pool is degraded (its raid5/RAIDZ so we can still access the pool and its data!) And it gives a hint on how to fix it.

A quick google, and the following command tells zfs to switch out the old disk, with the new one, and to then resilver. (I had to use -f to force it too, as my replacement disk had data and other bits on)

> zpool replace storage -f /dev/disk/by-id/ata-SAMSUNG\_HD501LJ\_S0MUJ13P651726 /dev/disk/by-id/ata-SAMSUNG\_HD501LJ\_S0MUJ13P651727

If you run

> $> zpool status
> 
> (only interesting parts of output included)
> 
> scan: resilver in progress since Sun Feb 23 10:19:11 2014
  
> 265M scanned out of 5.25G at 33.1M/s, 0h2m to go
  
> 86.2M resilvered, 4.92% done
> 
> replacing-2                                UNAVAIL      0     0     0
  
> ata-SAMSUNG\_HD501LJ\_S0MUJ13P651726       UNAVAIL      0     0     0
  
> ata-SAMSUNG\_HD501LJ\_S0MUJ13P651727       ONLINE       0     0     0  (resilvering)

About 3minutes later it finished, and running zpool status again, shows the zpool all backup and running again fine.

Quick and simple.

Now to validate the data is the same and correct.

&nbsp;