---
id: 224
title: 'Some code snippets from my home page: Part 1'
date: 2011-05-17T10:23:59+00:00
author: Lloyd Sparkes
layout: post
guid: http://blog.lloydsparkes.co.uk/?p=224
permalink: /2011/05/some-code-snippets-from-my-home-page-part-1/
aktt_notify_twitter:
  - 'yes'
categories:
  - Random Notes
  - Web Development
---
About 6 months ago i reorganized my website, this included a new homepage ( [here](http://lloydsparkes.co.uk) ). A lot of the code was borrowed from a friends web page ( [here](http://x5315.com/) ), recently a friend who likes it asked me how the code worked, and to go through it, so i thought it might be worth making a blog post on it.

All the code is under the license &#8220;Creative Commons Attribution-Noncommercial 2.0 UK: England & Wales License&#8221; and is copyright to [Tom Brearley](http://x5315.com).

I assume a basic knowledge of HTML / JavaScript.

There are 4 parts to the web page in question, the tag line, recent blog posts (items from an RSS feed), recent tweets(items from twitter), recent music (from last.fm).

All of the code requires jQuery, i used it from the Google CDN but you can use it locally. The code to use it from the Google CDN is:

\[javascript\]\[/javascript\]

Simply place this in the header of your HTML.

### The Tag Line

This is rather simple. We have an array of tag lines, and we pick on random when the page loads.

The first this we need is a placeholder for the final message. Insert it in to the body of the page. Also include a fall-back message, which will be displayed if for some reason the JavaScript fails.

[javascript]<span id="tagline">is awesome</span>[/javascript]

Then the code which will actually pick a tag line and insert it correctly into the document. In the head of the document, create a script tag, and insert the following function (modifying the tags to your taste). This simple function just creates an array called &#8220;phrases&#8221;. Then using the jQuery notation, sets the HTML property of the tag with the name &#8220;tagline&#8221; with a random phrase.
  
[javascript]
  
function go(){
  
var phrases = Array(
  
&#8220;uses <a href=&#8221;http://www.bing.com&#8221;>Bing!</a>&#8221;,
  
&#8220;loves <a href=&#8221;http://www.microsoft.com/windows&#8221;>Windows</a>&#8221;,
  
&#8220;uses <a href=&#8221;http://www.microsoft.com/ie&#8221;>Internet Explorer 9</a>&#8221;,
  
&#8220;loves <a href=&#8221;http://www.microsoft.com/windowsphone&#8221;>Windows Phone 7</a>&#8221;,
  
&#8220;uses <a href=&#8221;http://www.microsoft.com/windows&#8221;>Visual Studio 2010</a>&#8221;,
  
&#8220;is a <a href=&#8221;http://www.conservatives.com/default.aspx&#8221;>Conservative</a>&#8221;,
  
&#8220;reads <a href=&#8221;http://conservativehome.blogs.com/&#8221;>Conservative Home</a>&#8221;,
  
&#8220;dislikes <a href=&#8221;http://www.apple.com/macosx/&#8221;>OS X</a>&#8221;,
  
&#8220;loves his <a href=&#8221;http://www.apple.com/macbookpro/&#8221;>MacBook Pro</a>&#8221;,
  
&#8220;used to be a <a href=&#8221;http://en.wikipedia.org/wiki/Scouting&#8221;>Scout</a>&#8221;,
  
&#8220;programs in <a href=&#8221;http://en.wikipedia.org/wiki/C\_Sharp\_(programming_language)&#8221;>C#</a>&#8221;,
  
&#8220;prefers <a href=&#8221;http://en.wikipedia.org/wiki/Dogs&#8221;>dogs</a> over <a href=&#8221;http://en.wikipedia.org/wiki/Cat&#8221;>cats</a>&#8221;
  
)
  
$(&#8220;#tagline&#8221;).html( phrases[ Math.floor(Math.random() * phrases.length) ] )
  
}[/javascript]

Finally we need to call this function once the page is loaded. To do this insert the following code just before the &#8220;go()&#8221; function.
  
[javascript]
  
$(document).ready(function(){
  
go()
  
})
  
[/javascript]
  
And that is Part 1, watch out soon for the final 3 parts.