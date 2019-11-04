---
id: 827
title: 'jQHK: A study of the Parallax Effect'
date: 2012-03-01T02:22:32+00:00
author: caphun
layout: post
guid: http://www.yelotofu.com/?p=827
permalink: /2012/03/jqhk-a-study-of-the-parallax-effect/
categories:
  - CSS
  - JavaScript
  - jQuery
  - jQuery Hong Kong
tags:
  - jqhk
  - jqueryhk
  - jqueryhongkong
  - parallaxeffect
---
In our recent jQuery HK meetup we explored the technic behind the parallax effect using <a href="http://nikebetterworld.com/about" target="_blank">Nike Better World</a> as a reference for our live coding session.

The core idea of the effect is:

  1. bind each section, sprite and background to the window scroll event
  2. record the original offset of the element
  3. divide the scroll position by the desired speed of the element and discount the original offset value
  4. apply varying speeds to elements as desired to create the parallax effect
  5. for the nikebetterworld specific effect where the background image overlaps that&#8217;s done with `background-attachment: fixed`

<a href="http://jsbin.com/eyaviz/edit#javascript,html" target="_blank">Here&#8217;s what we came up with.</a>

N.B. Sorry about the Angry bird theme for those who try to run the script. That&#8217;s quite a big hit over here for Kongers of all age groups!<img src="http://localhost:8888/wp-includes/images/smilies/icon_biggrin.gif" alt=":D" class="wp-smiley" />