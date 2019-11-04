---
id: 64
title: CSS Diagnostics
date: 2008-03-27T12:13:31+00:00
author: caphun
layout: post
guid: http://yelotofu.com/2008/03/css-diagnostics/
permalink: /2008/03/css-diagnostics/
categories:
  - CSS
  - Tools
tags:
  - CSS
  - diagnostics
  - Tools
---
**What is CSS diagnostics?** It&#8217;s a method of applying styles to elements in your markup to catch standards compliance issues. A way of ensuring you don&#8217;t leave any serious accessibility holes and a visual deterrent for web authors editing pages with diagnostics switched on.

Here are some resources I found useful in understanding the practicality of this pioneering concept:

  * [Diagnostic styling](http://24ways.org/2007/diagnostic-styling)
  * [CSS Tools: Diagnostic CSS](http://meyerweb.com/eric/tools/css/diagnostics/)
  * [Helping your client maintain markup quality](http://www.456bereastreet.com/archive/200710/helping_your_client_maintain_markup_quality/)
  * [Find depreciated elements using CSS](http://snipplr.com/view/5194/css-diagnostics--find-depreciated-elements-using-css/)

The only problem with CSS diagnostics is that it relies on the CSS capabilities of a browser to find issues. So if your browser is less capable, meaning it doesn&#8217;t understand the diagnostic styles, then it negates the idea totally. Mind you, we&#8217;re at a point in CSS support whereby this is becoming less and less a problem but it is still a potential one.

Luckily CSS diagnostics isn&#8217;t the be all and end all of diagnostics. We have the king of diagnostics — [Firebug](http://www.getfirebug.com/), [Web Inspector](http://webkit.org/blog/108/yet-another-one-more-thing-a-new-web-inspector/) for Safari and more recently the much improved [IE8 Developer Toolbar.](http://blogs.msdn.com/ie/archive/2008/03/07/improved-productivity-through-internet-explorer-8-developer-tools.aspx) And if you&#8217;re looking for a cross-browser solution there&#8217;s always the brilliant [XRAY](http://westciv.com/xray/xray_more.html). Oh, how spoilt we all are!