---
id: 845
title: Reverse Inline Editing
date: 2012-03-11T20:34:15+00:00
author: caphun
layout: post
guid: http://www.yelotofu.com/?p=841
permalink: /2012/03/reverse-inline-editing/
dsq_thread_id:
  - "1241687261"
dsq_needs_sync:
  - "1"
categories:
  - JavaScript
  - Ramblings
tags:
  - editable
  - inlineedit
  - JavaScript
---
I want to throw this out there as I&#8217;m wondering if anyone is interested in a different approach to <a href="http://www.yelotofu.com/2009/08/jquery-inline-edit-tutorial/" target="_blank">making HTML elements editable</a>&#8230; I recently wrote some code that does the reverse of what my [existing inlineEdit plugin](https://github.com/caphun/jquery.inlineedit) does. i.e. it starts of as a form input element and turns into a placeholder on load. Once loaded up you can do all the same saving/canceling as the usual editable elements but the beauty now is that underneath it&#8217;s a plain old form element so degrades nicely if you also wish to cater for non-javascript users. So I wonder which approach is best? What are the pros and cons? Or should a plugin cater for both scenarios?