---
id: 561
title: Zend Server CE and Snow Leopard Problem
date: 2009-09-04T00:32:30+00:00
author: caphun
layout: post
guid: http://yelotofu.com/2009/09/zend-server-ce-and-snow-leopard-problem/
permalink: /2009/09/zend-server-ce-and-snow-leopard-problem/
dsq_thread_id:
  - "1304934527"
categories:
  - Ramblings
tags:
  - snowleopard
  - zendserver
  - zendserverce
---
There&#8217;s a compatibility issue with the Java Bridge in Zend Server CE which results in failure of the ZendServer admin interface. A temporary fix could be found at <http://forums.zend.com/viewtopic.php?f=44&t=1115>

I found this out the hard way &#8211; reinstalled and digged the internals before realizing it was a compatibility issue. I hope the Zend guys fix this soon!

Oh, I&#8217;m on Zend Server CE 4.0.5