---
id: 655
title: How to get Fancybox 1.3.1 to stay put!
date: 2010-06-07T12:11:41+00:00
author: caphun
layout: post
guid: http://yelotofu.com/?p=655
permalink: /2010/06/how-to-get-fancybox-1-3-1-to-stay-put/
dsq_thread_id:
  - "1241820093"
dsq_needs_sync:
  - "1"
categories:
  - Ramblings
---
I recently had a need to use a Fixed position overlay and found that Fancybox breaks if I set `#fancybox-wrap` to `position:fixed`. I believe the `centerOnScroll` option was supposed to solve this problem by recalculating the absolute position of `#fancybox-wrap` upon scrolling. The problem with this approach is that the overlay &#8216;shudders&#8217; or &#8216;feels jumpy&#8217; when you scroll in Firefox, Opera and IE7+.

Luckily the fix is actually pretty simple with the following steps:

**1. Get a copy of the source code** &#8211; [jquery.fancybox-1.3.1.zip](http://fancybox.googlecode.com/files/jquery.fancybox-1.3.1.zip)

**2. Do a in-code-search** 

Open jquery.fancybox-1.3.1.js and look for the `fancybox_get_viewport` function (should be around line 56), the function should look like this:

<pre language="javascript">fancybox_get_viewport = function() {
  return [ $(window).width(), $(window).height(), $(document).scrollLeft(), $(document).scrollTop() ];
},
</pre>

**3. Change it to look like this:**

<pre language="javascript">fancybox_get_viewport = function() {
  var isFixed = wrap.css('position') === 'fixed'; // add support for fixed positioning
  return [ $(window).width(), $(window).height(), isFixed ? 0 : $(document).scrollLeft(), isFixed ? 0 : $(document).scrollTop() ];
},
</pre>

**4. Add some CSS**

Add the following clauses to your CSS files (ensure these clauses load _after_ the jquery.fancybox-1.3.1.css file):

<pre language="css">#fancybox-wrap {
  position: fixed; 
}
* html #fancybox-wrap {	/* IE6 */
  position: absolute;
}
</pre>

That&#8217;s it!

Basically what the fix does is detect whether the wrapper is a fixed position element, if so it would return 0 for the scrollLeft and scrollTop values of the viewport. So even if you&#8217;re not using a fixed position element you can add this fix in as it&#8217;s non-destructive.