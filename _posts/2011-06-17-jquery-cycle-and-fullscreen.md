---
id: 752
title: jQuery Cycle and Fullscreen
date: 2011-06-17T22:57:37+00:00
author: caphun
layout: post
guid: http://yelotofu.com/?p=752
permalink: /2011/06/jquery-cycle-and-fullscreen/
dsq_thread_id:
  - "1241816929"
dsq_needs_sync:
  - "1"
categories:
  - JavaScript
  - jQuery
tags:
  - cycle
  - fullscreen
  - plugin
---
[jQuery Cycle](http://jquery.malsup.com/cycle/) is an excellent plugin and the most extensible jquery plugin I&#8217;ve seen thus far. It works surprisingly well and is very accommodating to all sorts of external html/css setups. 

However there is an itch to scratch when it comes to fullscreen sliding. The Cycle plugin doesn&#8217;t quite support this well enough. Fortunately the Transition Effects architecture allows us to write custom transitions to overcome this problem.

<pre language="javascript">/* Ca-Phun Ung &lt; caphun at tofugear dot com&gt;
 * Support for fullscreen horizontal scroll transitions.
 */
$.fn.cycle.transitions.scrollMaxHoriz = function($cont, $slides, opts) {
    var w = $(window).width();
    if (opts.minWidth && w &lt; opts.minWidth) w = opts.minWidth;
	opts.before.push(function(curr, next, opts, fwd) {
		if (opts.rev)
			fwd = !fwd;
        curr.cycleW = next.cycleW = w;
		$.fn.cycle.commonReset(curr,next,opts);
		opts.cssBefore.left = fwd ? (next.cycleW-1) : (1-next.cycleW);
		opts.animOut.left = fwd ? -curr.cycleW : curr.cycleW;
	});
	opts.cssFirst.left = 0;
	opts.cssBefore.top = 0;
	opts.animIn.left = 0;
	opts.animOut.top = 0;
};
</pre>

As you may notice in the above transition I&#8217;m only dealing with screen width hence I call this the scrollMaxHoriz transition. Now how to use this code? First load it as part of your javascript library stack then in your cycle call you can:

<pre language="javascript">$('.my-slides').cycle({
  fx: 'scrollMaxHoriz', // use custom scrollMax transition plugin
  minWidth: 1057 // optional
});
</pre>

That&#8217;s it!