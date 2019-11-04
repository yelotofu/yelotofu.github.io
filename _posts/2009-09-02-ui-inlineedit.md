---
id: 547
title: 'Labs: UI inlineEdit'
date: 2009-09-02T01:32:50+00:00
author: caphun
layout: post
guid: http://yelotofu.com/?p=547
permalink: /2009/09/ui-inlineedit/
dsq_thread_id:
  - "1265786865"
dsq_needs_sync:
  - "1"
categories:
  - JavaScript
tags:
  - in-place-edit
  - inline-edit
  - inlineedit
  - inplaceedit
  - JavaScript
  - jQuery
  - JQuery UI
  - jqueryui
---
After my last tutorial on building a simple [inlineEdit plugin](http://yelotofu.com/2009/08/jquery-inline-edit-tutorial/) I converted the concepts into a UI widget. It&#8217;s now sitting in labs for you to use, pick apart and devour:

[http://jquery-ui.googlecode.com/svn/branches/labs/inlineedit/demo.html  
](http://jquery-ui.googlecode.com/svn/branches/labs/inlineedit/demo.html) 

If you inspect the <a href="http://jquery-ui.googlecode.com/svn/branches/labs/inlineedit/ui.inlineEdit.js" target="_blank">source code</a> you will notice the structure is quite different. It&#8217;s actually pretty much the same functionality wise but I have separated each piece into smaller chunks. This makes it easier to extend in future (I plan to write more on ways to extend UI widgets in another post).

Here&#8217;s a quick peek at the features:

  * Basic inline editing &#8211; click, edit, save
  * Ability to save on pressing ENTER key
  * Cancel by un-focussing the input or clicking cancel
  * ThemeRoller ready
  * Customisable empty placeholder
  * Save and Cancel callbacks
  * Cancelable Save callback (so you could script a cancel action)

As usual please feedback and help improve this widget either by commenting here or on the [InlineEdit design & planning page](http://wiki.jqueryui.com/InlineEdit)

Enjoy!