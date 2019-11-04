---
id: 12
title: Xaraya xlink
date: 2006-11-13T08:55:32+00:00
author: caphun
layout: post
guid: http://yelotofu.com/blog/?p=5
permalink: /2006/11/xaraya-xlink/
dsq_needs_sync:
  - "1"
categories:
  - PHP
tags:
  - SEO
  - xaraya
  - xlink
---
Xaraya has a wonderful module called &#8220;xlink&#8221; which enables cross linking to module items. xlink makes it possible to specify an alternative URL for any module item just by hooking it to that module. What this means for SEO and migration in general is you can now keep your old URLs that bring traffic and not get penalized by search engines who are getting 404&#8242;s for content that was previously there. I had to modify the xlink module slightly though to ensure a 301 Moved Permanently is passed instead of the default 302 Moved Temporarily HTTP header.The only thing lacking with xlink at the time of writing is it does not have a &#8220;create&#8221; admin API function, there is only &#8220;createhook&#8221;. The problem with &#8220;createhook&#8221; is it only caters for one-to-one relationships between old URLs and a module item.

Hopefully this missing feature will be added to the next xlink release, meanwhile I will just stick to my own implementation of the &#8220;create&#8221; function.