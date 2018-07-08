---
id: 213
title: Windows and Software Installation
date: 2011-04-11T12:07:25+00:00
author: Lloyd Sparkes
layout: post
guid: http://blog.lloydsparkes.co.uk/?p=213
permalink: /2011/04/windows-and-software-installation/
aktt_notify_twitter:
  - 'yes'
categories:
  - Random Notes
---
In a number of recent discussions with some of my friends at university they complained that installing software on Windows is hard or complicated, or more so than it needs to be, or compared to their favorite operating system.

So in this post i aim to see if i can uncover what the issue is, and possible fixes for this issue. I will also look at the common ways of installing software on other platforms, and if they are better, or if they have similar issues.

### Windows &#8211; The Process (and Issues)

Installers on Windows generally work using a Wizard interface (Nullsoft, MSI), that after a sequence of steps, it then copies files to an appropriate place (hopefully %programfiles%) and registers its self with the system so it appears in Add/Remove programs.

One of the advantages of MSI is that it does a good job of managing upgrading previously installed software, without simply overwriting the old files (it will detect if a previous was installed, then remove the old version and install the new version), it can also be installed without a GUI which is good for corporate usage and systems management.

A few years ago Microsoft introduced a new system called Click Once. This installs an application in the users personal %appdata% directory which ensures security to an extent, due to this most applications can be installed by the user, without the help of an administrator. The final benefit to this new system is that it can do automatic application updates. Unfortunately very few developers have taken advantage of this method, although notable developers who have are Google who use it for chrome, and a large number of Twitter applications.

Uninstalling an application is rather simple, you just find it in Add/Remove Applications, then click uninstall. This can be slightly painful when it comes to big complex bits of software like Visual Studio that have a large number of different components to be un-installed in turn.

The only other time un-installation can be a problem, is if an older application uses an installer that does not register its self properly, it can sometimes be a bit of a pain to find the uninstaller.

There are a number of issues when it comes to software installation on Windows. The first is that there are a large number of inconsistent installation systems that developers use, and they all provide a number of different features and work in slightly different ways, but the key here is that there is no consistency in what the user can expect.

One thing that i must mention here is that now most installation systems actually use MSI (Windows Installer or Microsoft Installer) underneath but present the user with a special GUI, but there are still plenty of developers using the Nullsoft system especially in the open source arena.

**Pros:** 
  
**General &#8211; Good management of Uninstallers**
  
**Click Once &#8211; Automated Updater, Simple only a few clicks, doesn&#8217;t require administrator permissions**
  
**MSI &#8211; Scriptable, Software versioning**

**Cons:**
  
**General &#8211; Inconsistent UI, a large number of legacy installers, complex software can make uninstalling painful having to uninstall each sub package manually.**

### Mac OS X &#8211; The Process (and Issues)

OS X is actually very similar to Windows but i will just go through it, but there are a number of ways.

The first way, that is most widely used is a .app file(although its actually a folder) for distribution, this can be downloaded directly, or be distributed in a .dmg file, then drag it into the &#8220;Applications&#8221; folder (or any where else if the user does not have permission to the Applications folder). The App Store automates this process even further.

The second method is to use a .pkg or .mpkg installer. From my research this is simply a modified .tar.gz file, with a special folder structure. .mpkg installers can also be used to install a number of .pkg&#8217;s. The way its done means that Apple provide the installer GUI so it is always consistent, but it can also be scripted.

The final way you can install software is the &#8220;Unix&#8221; from source way. You can do your usual &#8220;./configure && make && make install&#8221;.

Un-installation and clearing up from some programs can be a bit problematic though. To remove a .app installed program you just delete the .app file, although this will leave the application preferences behind which you may want to manually clean up. To uninstall a .pkg or .mpkg it can be slightly more problematic, generally having to find and execute a script to do the heavy lifting for you and the same for reversing the &#8220;Unix&#8221; way of installing software.

None of their installers have a way for automated updating, but there is a 3rd party library that is widely used called Sparkle. The new App Store also handles updating automatically.

**Pros:**
  
 **.app &#8211; Simple Install / Uninstall**
  
 **.pkg/.mpkg &#8211; Consistent UI**

**Cons:**
  
 **.app &#8211; Uninstall leaves user specific application data behind**
  
 **.pkg/.mpkg &#8211; Needs a script to uninstall**

### Linux &#8211; The Process (and Issues)

On Linux you generally have three options. Install the &#8220;Unix&#8221; way from source, which we have already discussed with OS X. Install using the package manager from repositories OR install using a package manager and a manually downloaded package.

The later two ways make installation and un-installation fairly easy (through command line or a GUI). They are also a good way to distribute updates.

But there are problems with this, the repositories do not tend to stay up to date with the latest versions of the software, but may be a few versions behind. This leads to using the other installation options to get the latest versions, which complicate the management of installed software. Although this is not so much of an issue where servers are concerned where stable software is ensured through the repositories. The other problem left is that the &#8220;official&#8221; methods of installing software is restricted to users with root permissions although they can install and setup software manually within their own directories, although this can be very complicated.

**Pros:**
  
**Stability, security.**

**Cons:**
  
**Out of date locked down to just users with root/sudo permissions**

### What can Microsoft do?

So Microsoft and Windows is actually already in pretty good shape, and with the Windows App Store, this should solve a large number of the inconsistencies, and it should also handle updating.

But there is more Microsoft can do. They need to really push tools and software to work with Click Once and MSI with detailed documentation on why developers should use them, and which one is suitable for their particular application.

It should be a rather simple sell and distinction between what to use for different programs.

Click Once should be used for utility applications, so twitter clients, irc clients, ftp, paint (yes you Paint.Net), notepad, putty (just putty, not the rest of the suite)

MSI&#8217;s should be used for software that requires to be installed system wide, larger installations, and software which requires background services, system services, or have some complexity which means they might not be suitable for Click Once, so for example, Office, Visual Studio, Putty (with pageant)

They should enforce a single consistent UI for MSI&#8217;s which would help users, and provide some consistency for the user.

They also need to have a global update center, where everything installed can register itself (including MS software updated through Windows Update) so that all updates are centralized, and easy for the user to access, and the developers to take advantage of.

Finally they should improve the Add/Remove Programs files, so that when applications like Visual Studio is installed all the sub-packages are hidden beneath the top level as to simply the window. It might also be beneficial to separate applications into just the Click Once ones they installed, and the applications which are installed globally.