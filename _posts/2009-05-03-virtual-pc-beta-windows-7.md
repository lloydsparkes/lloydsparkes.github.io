---
id: 25
title: Virtual PC Beta (Windows 7)
date: 2009-05-03T21:08:41+00:00
author: Lloyd Sparkes
layout: post
guid: http://lloydsparkes.co.uk/?p=25
permalink: /2009/05/virtual-pc-beta-windows-7/
categories:
  - Beta
  - Virtual PC
  - Windows 7
  - XP Mode
---
Due to be publicly released on Tuesday (5th May 2009), the new &#8216;Windows Virtual PC&#8217; Beta is a massive improvement over Virtual PC 2007.

I have various VM&#8217;s which are mostly used for playing with Ubuntu for when i need to compile something on Linux, and more frequently XP for testing the [Dokan](http://dokan-dev.net/en/) driver (which is heavily used in one of my forthcoming projects).

From the playing around i did yesterday, the VM’s seem more responsive, and the resource overhead seems a lot less than before. Another improvement is the Integration components. On the &#8216;XP Mode&#8217; VM they worked instantly, and allowed much more fluid interaction with the host system, including guest OS searching, and file transfers, and of course the new transparency of running applications from the VM like they were on the desktop.

Problems I had:

I couldn’t &#8216;upgrade&#8217; my settings files to the new format, if the machine had had its state saved(not shutdown).

Also upgrading the integration components from Virtual PC 2007 to the new ones, in a XP VM required 3 reboots, and was rather messy.

I couldn’t shutdown the XP Mode VM i could only disconnect, (you can get around this using the command line). This caused a problem when trying to change how much ram the VM had as it needs to be properly shut down before this setting can be changed.

Apart from that it’s a good all round product, that works really well. My favourite feature is how it creates a new top level user folder, and to manage your VM&#8217;s you use this through explorer, which really is a lovely touch(see image below), and i hope to &#8220;copy&#8221; this level of integration in one of my forthcoming projects.

<img class="alignnone size-full wp-image-26" title="Virtual PC Beta Integration in Windows 7" src="http://blog.lloydsparkes.co.uk/wp-content/uploads/2009/05/untitled.png" alt="Virtual PC Beta Integration in Windows 7" width="803" height="546" srcset="https://lloydsparkes.co.uk/wp-content/uploads/2009/05/untitled.png 803w, https://lloydsparkes.co.uk/wp-content/uploads/2009/05/untitled-300x203.png 300w" sizes="(max-width: 803px) 100vw, 803px" />

Intel users beware: Windows Virtual PC requires Intel-VT, which is available on random processors throughout their product line, so check that you have this feature, and it is enabled in the bios, before trying to use this product.