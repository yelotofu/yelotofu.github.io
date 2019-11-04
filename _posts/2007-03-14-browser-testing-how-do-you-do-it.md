---
id: 30
title: 'Browser testing: How do you do it?'
date: 2007-03-14T00:18:29+00:00
author: caphun
layout: post
guid: http://yelotofu.com/2007/03/browser-testing-how-do-you-do-it/
permalink: /2007/03/browser-testing-how-do-you-do-it/
categories:
  - Browser Testing
tags:
  - andy clarke
  - browser testing order
  - browsers
---
Andy Clarke, the author of [Transcending CSS](http://www.transcendingcss.com/), started an interesting discussion on [CSS Browser Testing Order](http://www.stuffandnonsense.co.uk/archives/css_browser_testing_order.html). It&#8217;s surprising how we more or less test in the same order. I place Windows XP first though as I&#8217;m primarily a windows user and my clients are usually on Windows too.**My CSS browser testing order**

  1. Firefox / Opera on Win XP
  2. Internet Explorer 7 on Win XP
  3. Safari / Firefox on OSX
  4. Netscape 7 & 8 on Win XP
  5. Internet Explorer 6 on Win XP

I don&#8217;t usually worry about browsers older than those listed above unless the client has a specific requirement. I&#8217;ve also found that Safari renders as if it were a cross between Firefox & Opera on Windows XP, so if it looks good in both browsers it should look near perfect in Safari on OSX.

As you may well have noticed, IE6 is last. The rule of the game is to test your browsers in order of most compliant then work around the lesser compliant ones and even use a hack or two for those that refuse to obeyâ€”namely IE6. If you test your work with this mindset, browser testing would never be a nightmare and may even be fun! Well, sometimes fun.<img src="http://localhost:8888/wp-includes/images/smilies/icon_wink.gif" alt=";)" class="wp-smiley" /> 

This testing order is by no means a rule of thumb, it&#8217;s just the way that works for me. I&#8217;d be interested to hear how you do it.