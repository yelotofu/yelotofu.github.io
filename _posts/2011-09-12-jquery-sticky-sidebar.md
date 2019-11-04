---
id: 781
title: jQuery Sticky Sidebar
date: 2011-09-12T02:00:00+00:00
author: caphun
layout: post
guid: http://www.yelotofu.com/?p=781
permalink: /2011/09/jquery-sticky-sidebar/
dsq_thread_id:
  - "1241711125"
dsq_needs_sync:
  - "1"
categories:
  - JavaScript
  - jQuery
tags:
  - jquerystickysidebar
  - stickysidebar
---
This is something I wrote in a few hours so thought I&#8217;d share it with the world. It mimics the sidebar UX seen on Apple and Amazons purchase flows. I tried to keep this as simple as possible. There are two states the plugin determines &#8211; Sticky and non-Sticky. When the Sidebar is sticky its `position:fixed`, when non-Sticky it&#8217;s `position:absolute`. The plugin determines one or the other by checking where you&#8217;ve scrolled to. The window of stickiness starts from the point you past the adjacent main content up until the sidebar reaches the bottom of the adjacent main content. <a href="http://htmlpreview.github.com/?https://github.com/caphun/jquery.stickysidebar/blob/master/demo.html" target="_blank">Check the demo and all will be clear!</a>

Source code on github at  
<a href="https://github.com/caphun/jquery.stickysidebar" target="_blank">https://github.com/caphun/jquery.stickysidebar</a>

Enjoy!<img src="http://localhost:8888/wp-includes/images/smilies/icon_smile.gif" alt=":)" class="wp-smiley" />