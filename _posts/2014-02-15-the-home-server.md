---
id: 319
title: The Home Server
date: 2014-02-15T16:46:01+00:00
author: Lloyd Sparkes
layout: post
guid: http://blog.lloydsparkes.co.uk/?p=319
permalink: /2014/02/the-home-server/
categories:
  - Linux
  - NAS
  - Plex Media Server
  - Random Notes
  - Technology
  - ZFS
---
Last year I decided not to renew my TV License for a myriad of reasons. This has lead me to using Netflix and my considerable DVD and TV/Movie collection a lot more.

I also want to share this content with my other devices remotely, and reliably. Basically what I want is a Netflix but for my collection! My NAS (Synology DS411j) is not powerful enough at the moment to do this, even before we consider transcoding content, and the more advance backup scenarios I would like.

So I then thought that using a AMD A4 CPU, I could build my own HTPC/NAS which could handle this for me. This was 1, looking rather expensive, both in terms of parts (a case which supported 4HDD&#8217;s is at least £100) and 2, in power usage.

It was then suggested that I could use a HP N54L micro server which would be able to handle (a colleague with the N36L/N40L could do it, so a N54L should be able to, too) the transcoding, needed for Plex Media Server. Its also significantly cheaper than building something myself, and its power usage is also wonderfully low.

A HP N54L micro server can be got for around £199, you can then get £100 cashback on top of that. So just £99! which is cheaper than a good case (and it comes with a pretty good case).

On top of that, I am adding 16GB of RAM (£115) So a total of £214. Hopefully I can get £100 for my old NAS which means I my outlay is only about £115, which isn&#8217;t bad really!

The boot drive will be either the 250GB HDD that comes with the micro server OR a spare 128GB SSD that I have, but I have not decided yet.

I&#8217;m going to write a little series, of blog posts as I set it up, the various tools and servers I use, with the custom scripts and bits I plan to use. I will be testing various failure scenarios and how to recover from them (mainly losing a disk, and replacing it). Hopefully by putting them online, they will help someone else, but also help me a few years down the road when I may need it.

So here&#8217;s the unspecific list of things I hope to blog about.

  1. [Modding the N54L&#8217;s BIOS to enable the extra SATA Ports](http://blog.lloydsparkes.co.uk/2014/02/the-home-server-part-1-modding-the-bios/)
  2. [Installing Ubuntu Server 13.10 & Setting up ZFS](http://blog.lloydsparkes.co.uk/2014/02/the-home-server-part-2-ubuntu-zfs/)
  3. [Recovering ZFS from a Drive Failure (simulated by pulling a drive out and wiping it)](http://blog.lloydsparkes.co.uk/2014/02/the-home-server-part-3-zfs-recovery/)
  4. SMB Setup
  5. RSync Backup from Clients & Snapshotting
  6. Snapshotting & Clean up
  7. Anything else that comes up long the way

&nbsp;

&nbsp;