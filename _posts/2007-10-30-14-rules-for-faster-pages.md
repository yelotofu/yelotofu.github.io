---
id: 52
title: 14 rules for faster pages
date: 2007-10-30T01:27:58+00:00
author: caphun
layout: post
guid: http://yelotofu.com/2007/10/the-14-rules-of-high-performance-websites/
permalink: /2007/10/14-rules-for-faster-pages/
categories:
  - Optimisation
tags:
  - 14rules
  - fasterwebpages
  - Optimisation
  - yslow
---
Steve Souders, chief of Yahoo&#8217;s Exceptional Performance Team, devised [14 rules for faster pages](http://developer.yahoo.com/performance/rules.html) to squeeze more zest from page performance, the rules in short are:

  1. Make Fewer HTTP Requests
  2. Use a Content Delivery Network (CDN)
  3. Add an Expires Header
  4. Gzip Components
  5. Put Stylesheets at the Top
  6. Put Scripts at the Bottom
  7. Avoid CSS Expressions
  8. Make JavaScript and CSS External
  9. Reduce DNS Lookups
 10. Minify JavaScript
 11. Avoid Redirects
 12. Remove Duplicate Scripts
 13. Configure ETags
 14. Make Ajax Cacheable

After sourcing through numerous high traffic sites they discovered that on average only 12% of a page request is used up by back-end processes whereas the remaining 88% is used up by front-end processes, such as JavaScript, CSS, Ajax and parsing the DOM. This is an interesting analysis but not at all surprising.

Yahoo have also released a handy Firefox plug-in called [YSlow](http://developer.yahoo.com/yslow/) which parses a web page and gives you performance analysis based on these 14 rules.