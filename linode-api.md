---
id: 145
title: 'Linode API C#'
date: 2010-02-12T19:13:56+00:00
author: Lloyd Sparkes
layout: page
guid: http://lloydsparkes.co.uk/?page_id=145
---
[Linode is &#8220;THE&#8221; best Linux VPS provider i have ever used](https://www.linode.com/?r=3c20ff729d165312409977c8d4abcaf279ccb0a1). I am currently working on a set of C#/Mono tools to manage my server part of this requires me to interact with their Linode API.

The current version is very basic, and I plan to improve it by adding Exception Handling, and a much improved LinodeResponse class.

I have hosted it on github [here](https://github.com/lloydsparkes/linode-api).

My Implementation is based fairly heavily on [Theodore Nguyen-Cao](http://github.com/theo/linode-api)&#8216;s Java Implementation. It is also released under the MIT License which means you can pretty much do what you like with the code. I also used [Json.Net](http://www.codeplex.com/Json) to handle the Json which is also under the MIT License.