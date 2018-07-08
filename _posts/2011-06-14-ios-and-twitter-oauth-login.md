---
id: 279
title: iOS and Twitter OAuth Login
date: 2011-06-14T16:26:24+00:00
author: Lloyd Sparkes
layout: post
guid: http://blog.lloydsparkes.co.uk/?p=279
permalink: /2011/06/ios-and-twitter-oauth-login/
aktt_notify_twitter:
  - 'yes'
aktt_tweeted:
  - "1"
categories:
  - Apple
  - C / C++
  - Twitter
---
I have recently been working on a iOS (iPhone) application for a client. This app needed to have the ability to post things to Twitter and Facebook.

Facebook provides a really nice SDK which (with a few hacks) provides an inline login dialog which handles all the oAuth details for you. It looks good and works well.

Twitter unfortunately does not do the same and while there are hundreds of Twitter-iOS libraries out there, they are all overly complicated and provide a UI which is not consistent with how the Facebook SDK does things, which if i want my app to appear good and consistent then they must look and behave the same.

The other main reason was because the libraries were overly complicated, they used the &#8220;Out of band&#8221; oAuth authentication which means a user has to copy a pin from a web page into the application, which is hardly a nice thing to do. Yet Facebook doesn&#8217;t have to do this. After a bit of investigation i found out twitter didn&#8217;t have to either.

To solve all of this i have created a simple demo application and library, utilizing the [Facebook-iOS-SDK](https://github.com/facebook/facebook-ios-sdk) and [PlainOAuth (by Jaanus Kase)](https://github.com/jaanus/PlainOAuth) projects as a basis and building what i wanted on top.

A lot of the code should be self explanatory. And below is a screen shot of what the end result is. You can find the project on git hub here: <https://github.com/lloydsparkes/unoffical-twitter-sdk>

<img class="aligncenter" title="Unoffical Twitter iOS SDK" src="http://lloydsparkes.co.uk/files/twitterios.png" alt="" width="330" height="640" />