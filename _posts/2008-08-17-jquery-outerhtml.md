---
id: 94
title: 'jQuery: outerHTML'
date: 2008-08-17T00:01:34+00:00
author: caphun
layout: post
guid: http://yelotofu.com/?p=94
permalink: /2008/08/jquery-outerhtml/
dsq_thread_id:
  - "1241832580"
dsq_needs_sync:
  - "1"
categories:
  - JavaScript
tags:
  - bits
  - jQuery
  - outerhtml
  - plugin
  - snippet
---
The outerHTML property (IE only) could sometimes be very handy, especially if you&#8217;re trying to replace an element entirely. [Brandon Aaron](http://blog.brandonaaron.net) has very kindly given us a [outerHTML plugin](http://blog.brandonaaron.net/2007/06/17/jquery-snippets-outerhtml/) that does half the job as it doesn&#8217;t support replacements. The following code snippet fills in the blanks:

<pre language="javascript">jQuery.fn.outerHTML = function(s) {
return (s)
? this.before(s).remove()
: jQuery("&lt;p&gt;").append(this.eq(0).clone()).html();
}
</pre>

To get the outerHTML value of an element do this&#8230;

<pre language="javascript">$('#myTag').outerHTML();
</pre>

To replace #myTag entirely do this&#8230;

<pre language="javascript">$('#myTag').outerHTML("&lt;p&gt;My brand new #myTag.&lt;/p&gt;");
</pre>

Hope this helps someone<img src="http://localhost:8888/wp-includes/images/smilies/icon_smile.gif" alt=":)" class="wp-smiley" /> 

**Update:** There&#8217;s now a [demo page](http://yelotofu.com/labs/jquery/snippets/outerhtml/demo.html).