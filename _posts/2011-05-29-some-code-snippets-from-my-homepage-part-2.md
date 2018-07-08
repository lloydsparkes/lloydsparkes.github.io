---
id: 274
title: 'Some code snippets from my homepage: Part 2'
date: 2011-05-29T17:58:06+00:00
author: Lloyd Sparkes
layout: post
guid: http://blog.lloydsparkes.co.uk/?p=274
permalink: /2011/05/some-code-snippets-from-my-homepage-part-2/
aktt_notify_twitter:
  - 'yes'
aktt_tweeted:
  - "1"
categories:
  - Technology
---
In this part 2 of my series on the various parts i used to build my new homepage for my website i will cover how i put my RSS feeds on the page.

Again to start with you will need to use jQuery and the Google JavaScript API. So insert the following two lines into the header of your HTML if you do not already have them included. You can also substitute the jQuery import from the Google CDN with a local address or another CDN.

[javascript]
  

  

  
[/javascript]

The next bit is we need a place holder so somewhere in the body of the document

[javascript]

<div id="blog">
  <h3>
    Recent Blog Posts
  </h3>
</div>

[/javascript]

Then we just need the following function to fetch the last entries, then to write them out into the placeholder:

[javascript]
  

  
[/javascript]
  
Finally the ready function so when the document is ready the function will be executed and the feed entries into the page.

[javascript]
  

  
[/javascript]

And thats loading a RSS feed into a page using JavaScript.