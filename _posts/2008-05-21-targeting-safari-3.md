---
id: 91
title: Targeting Safari 3
date: 2008-05-21T05:23:54+00:00
author: caphun
layout: post
guid: http://yelotofu.com/?p=91
permalink: /2008/05/targeting-safari-3/
categories:
  - CSS
tags:
  - CSS
  - csshacks
  - hacks
  - safari
  - safari3
---
Found [this CSS hack for Safari 3](http://dustinbrewer.com/css-hackgetting-safari-to-behave/) today which can be handy from time to time:

<pre language="css">@media screen and (-webkit-min-device-pixel-ratio:0){
    /* Safari 3 specific styles go here */
}
</pre>

Most of the time if something looks good in Firefox 2 there&#8217;s a 99% chance it will in Safari 3 too. So use this hack sparingly and only when absolutely necessary.