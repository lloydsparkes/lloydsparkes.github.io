---
id: 156
title: Windows Phone 7 and Gaming
date: 2010-08-09T17:50:35+00:00
author: Lloyd Sparkes
layout: post
guid: http://lloydsparkes.co.uk/?p=156
permalink: /2010/08/windows-phone-7-and-gaming/
categories:
  - Beta
  - Windows Phone 7
  - XNA
---
I am currently lodging out in the countryside for my summer job, and I found my ideas list and decided to work on the WP7 games I have had ideas for. So armed with my “craptastic” laptop, Visual Studio + Windows Phone 7 Dev Tools Beta i started to write my first game, which i hope will be done by the end of August/mid September in time for the Windows Phone 7 release so i can sell it on the marketplace [(Students can sign-up here for the marketplace FREE)](https://www.dreamspark.com/Products/Product.aspx?ProductId=28).

I am just going to go through some of my experiences as a developer taking my first serious look at this platform and the problems I encountered in the last 6 hours. I would just like to say as well this is my first time using XNA.

## Hello World

So i sat down and decided to setup a simple program which prints Hello World to the screen. The first problem i encountered was how to force the screen into landscape orientation. I had a look around and apparently this was not possible in the CTP and CTP-Refresh, so i decided to just use the TouchPanel.DisplayOrientation and set it to LandscapeLeft and to test if that worked in the beta.

My only other experience of writing graphics applications was term where we had to use OpenGL/C to code a little program, and it was quite horrendous work to draw text to the screen, but i was pleasantly surprised by how easy and flexible it is to draw text to the screen in XNA, although i would prefer to only load one font, and change the size, rather than loading a new font for each required text size.

## Pressing F5

This is the bit where everything went a bit wrong. While the Emulator would start, i was not allowed to run any XNA applications because my graphics card was not good enough(I’m currently using a 3 year old HP 530 laptop for my main PC). After a bit of searching i found a way to disable checking of this in the emulator.

Under HKEY\_Local\_Machine\SOFTWARE\Microsoft\XDE create the key XNAEnableGPU (DWORD) and set it to 1.

Unfortunately my hardware really is incapable of running XNA games in the emulator and all i got was a black screen (the program was set to make the background Cornflower Blue by default). This also meant i was unable to test if the screen orientation was correct.

## Option 2

Luckily is takes mere seconds to port an application to Windows or the Xbox so for now i will be developing it on Windows, and then when i either get home, or i get hold of a Windows Phone 7 device, i can just port it back across and add support for the Windows Phone 7 controls.

I learn that when you use the “Create a copy for Windows” in Visual Studio that it keeps all the code in sync across the projects for each platform, so if you have some device dependant code (think input control, mouse vs. gamepad vs. touch screen) you just have to wrap it in

#if <platform name>

> code for this particular platform

#endif

Another really useful feature that i found is that you can switch graphics profiles on Windows XNA Games, between Hi Def and Reach. So as i want my application to work on WP7 straight away and my current graphics hardware is crap, i am using the Reach profile which works across all devices, while the Hi Def profile has features which only work on Windows or the Xbox.

## My Game

I have then spent 3 hours getting used to programming in XNA and while these are some very rough beginnings of my game here are some screenshots of what i have started. I still have a long way to go so watch this space.

By next week i hope to have a lot more of the game play and input controls working and some nicer screenshots and as i go along i will improve the graphics and artwork as these are based on some i just found on the internet

Like all Microsoft products, WP7 has a brilliant set of development tools and i suspect they are only going to get better with time, and with all the device leaks at the moment I&#8217;m starting to get quite excited about the launch

PS. If anyone from Microsoft would like to give me / lend me a WP7 device please contact me at @lloydsparkes on Twitter

[<img class="wlDisabledImage" style="display: inline; border: 0px;" title="Menu Screenshot" src="http://blog.lloydsparkes.co.uk/wp-content/uploads/WindowsPhone7andGaming_EDEA/MenuShot1_thumb_3.png" border="0" alt="Menu Screenshot" width="648" height="409" />](http://blog.lloydsparkes.co.uk/wp-content/uploads/WindowsPhone7andGaming_EDEA/MenuShot1.png)

[<img class="wlDisabledImage" style="display: inline; border: 0px;" title="Game Screenshot" src="http://blog.lloydsparkes.co.uk/wp-content/uploads/WindowsPhone7andGaming_EDEA/GamePlay1_thumb.png" border="0" alt="Game Screenshot" width="658" height="418" />](http://blog.lloydsparkes.co.uk/wp-content/uploads/WindowsPhone7andGaming_EDEA/GamePlay1.png)