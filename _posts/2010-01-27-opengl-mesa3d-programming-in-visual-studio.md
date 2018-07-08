---
id: 139
title: OpenGL / Mesa3D programming in Visual Studio
date: 2010-01-27T18:47:47+00:00
author: Lloyd Sparkes
layout: post
guid: http://lloydsparkes.co.uk/2010/01/27/opengl-mesa3d-programming-in-visual-studio/
permalink: /2010/01/opengl-mesa3d-programming-in-visual-studio/
categories:
  - C / C++
  - CGV
  - Computer Science
  - OpenGL
  - Random Notes
  - University of York
  - Visual Studio
  - Visual Studio 2010
---
**Update:** You will need to move the various .dll files into your project folder so they are in the path of the application, otherwise you will get missing DLL errors.

I am currently taking the Computer Graphics and Visualisation module at university and it require writing some programs in C using OpenGL / Mesa3D. Unfortunately the guides and tutorials they give on how to do it on Windows are from 1997, so i have decided to update them for 2010.

In this tutorial i am using Mesa3D 7.6.1, Visual Studio 2008. It also works with Visual Studio 2010 Beta 2.

The first step is to either download the Mesa3D Binaries from [here](http://blog.lloydsparkes.co.uk/files/Mesa3D.zip) or to compile them from source (compiling from source is pretty simple). Then extract the file somewhere sensible.

The second step is to setup a Visual Studio project so we can actually code something.

First create a new ‘Win32 Console Application’:

[<img style="display: inline; border: 0px;" title="image" src="http://blog.lloydsparkes.co.uk/wp-content/uploads/2010/01/image_thumb.png" border="0" alt="image" width="644" height="456" />](http://blog.lloydsparkes.co.uk/wp-content/uploads/2010/01/image.png)

Then choose your options. I’m picking a Empty project for this, but modify the options to what ever your needs are.

[<img style="display: inline; border: 0px;" title="image" src="http://blog.lloydsparkes.co.uk/wp-content/uploads/2010/01/image_thumb1.png" border="0" alt="image" width="644" height="457" />](http://blog.lloydsparkes.co.uk/wp-content/uploads/2010/01/image1.png)

Click finish then we, and we have our newly created project. Now we need to make a few changes, to include the additional libraries, and header files we require.

[<img style="display: inline; border: 0px;" title="image" src="http://blog.lloydsparkes.co.uk/wp-content/uploads/2010/01/image_thumb2.png" border="0" alt="image" width="644" height="458" />](http://blog.lloydsparkes.co.uk/wp-content/uploads/2010/01/image2.png)

Open up project properties. Then under ‘Configuration Properties’->‘C/C’++->’General’ you have the ‘Additional Include Directories’ setting, open this up, and add a folder, and navigate to your Mesa3D folder and select the ‘include’ directory.

_It has been noted that you need to have at least ONE .c / .cpp / .h file in your project for the C/C++ options to become available._

[<img style="display: inline; border: 0px;" title="image" src="http://blog.lloydsparkes.co.uk/wp-content/uploads/2010/01/image_thumb3.png" border="0" alt="image" width="644" height="467" />](http://blog.lloydsparkes.co.uk/wp-content/uploads/2010/01/image3.png)

Then go back to project properties, now under ‘Configuration Properties’->‘Linker’->’General’ you have the ‘Additional Library Directories’ setting, open this up, and add a folder, and navigate to your Mesa3D folder and select the ‘lib’ directory.

[<img style="display: inline; border: 0px;" title="image" src="http://blog.lloydsparkes.co.uk/wp-content/uploads/2010/01/image_thumb4.png" border="0" alt="image" width="644" height="450" />](http://blog.lloydsparkes.co.uk/wp-content/uploads/2010/01/image4.png)

Now you can do your coding as you like. Import code straight from your Linux projects (Use ‘Add Existing Items’) and it should compile fine if you have done everything correctly.

Anyway i hope this helps someone, if you have any comments for potential improvements or problems you are having, then please leave a comment and i will try to help out.