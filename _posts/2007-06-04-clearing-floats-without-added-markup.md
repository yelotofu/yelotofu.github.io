---
id: 34
title: Clearing floats without added markup
date: 2007-06-04T13:09:07+00:00
author: caphun
layout: post
guid: http://yelotofu.com/2007/06/clearing-floats-without-added-markup/
permalink: /2007/06/clearing-floats-without-added-markup/
categories:
  - CSS
tags:
  - andy clarke
  - clearing floats
  - transcending css
---
When floating an element it is taken out of the document flow. As a result, anything containing the floated element does not take on its width or height. Like most developers, to overcome this problem I applied an extra clearing DIV below the floated element. But this isn&#8217;t ideal as it just added more unmeaningful elements to the HTML document.Luckily there&#8217;s a nice alternative. Just apply an overflow:hidden CSS rule to the floated elements parent container, problem solved! This has the same effect as the above but without the added markup. Miles better I must say.

I found this little gem in Andy Clarke&#8217;s book: [Transcending CSS](http://www.transcendingcss.com/).