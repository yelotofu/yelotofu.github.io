---
id: 93
title: jQuery Numeric Stepper
date: 2008-07-21T03:19:01+00:00
author: caphun
layout: post
guid: http://yelotofu.com/?p=93
permalink: /2008/07/jquery-numeric-stepper/
dsq_thread_id:
  - "1243223764"
dsq_needs_sync:
  - "1"
categories:
  - Accessibility
  - JavaScript
tags:
  - JavaScript
  - jQuery
  - numericstepper
  - spinner
  - stepper
  - ui
  - widget
---
As an experiement I ported over my [Accessible Numeric Stepper](http://yelotofu.com/2007/07/building-an-unobtrusive-accessible-and-standards-compliant-numeric-stepper/) into a jQuery widget and added some accessibility enhancements and new features in the process.

This widget utilises [ui.core.js](http://docs.jquery.com/UI/Developer_Guide) &#8211; a factory method object for creating widget classes. Widgets in jQuery are essentially plugins at heart but built to follow stricter coding standards in order to unify the underlying quality between developers. It also adds convenient mouse interaction classes and option settings among other things.

The result is [jQuery Numeric Stepper](http://yelotofu.com/labs/jquery/UI/stepper/) an unofficial jQuery UI widget. Features include:

  * min, max, start and step size settings
  * supports decimal values and decimal step sizes
  * supports currency values
  * keyboard and mousewheel interaction &#8211; increment/decrement values via cursor keys, <kbd>+</kbd>/<kbd>-</kbd> keys and mousewheel

[Download latest source code here](http://yelotofu.com/labs/jquery/UI/stepper/jquery.ui.stepper-latest.zip)

Bugs? Missing feature? Code improvements? Let me know!

**Update:** Features seen here are now part of the official jQuery UI Spinner, set for the 1.6 release of jQuery UI. [More details](http://yelotofu.com/2008/08/jquery-ui-spinner/).