---
id: 250
title: 'jQuery: how to tell if you&#8217;re scroll to bottom?'
date: 2008-10-12T04:36:57+00:00
author: caphun
layout: post
guid: http://yelotofu.com/?p=250
permalink: /2008/10/jquery-how-to-tell-if-youre-scroll-to-bottom/
dsq_thread_id:
  - "1241858495"
dsq_needs_sync:
  - "1"
categories:
  - Ramblings
tags:
  - jQuery
  - scrollbottom
  - scrollheight
  - scrolltop
---
This is a question a jQuery user asked recently. It&#8217;s a simple question without a simple answer. There is no inverse equivalent to `scrollTop=0` (i.e. `scrollBottom=0`) so the solution requires some thought.

The scenario is this &mdash; we have a fixed height `div` with `overflow:auto` and we want to use JavaScript to programmatically scroll to bottom and also to execute some code if we&#8217;re at the bottom. Our `div` looks like this (using inline styles for the sake of this example):

<pre language="html">&lt;div id="box" style="height:300px; overflow:auto;"&gt;
  &lt;!-- Your content goes here --&gt;
&lt;/div&gt;
</pre>

To scroll to bottom programmatically we do:

<pre language="javascript">$('#box').animate({scrollTop: $('#box')[0].scrollHeight});
</pre>

And to check whether we&#8217;re scrolled to bottom:

<pre language="javascript">var elem = $('#box');
if (elem[0].scrollHeight - elem.scrollTop() == elem.outerHeight()) {
  // We're at the bottom.
}
</pre>

That&#8217;s pretty easy, right? As noticed `scrollHeight` is the key to this solution.

A bit of info about `scrollHeight`: First introduced by MSIE and supported since version 4, <sup><a href="http://msdn.microsoft.com/en-us/library/ms534615(VS.85).aspx">[1]</a></sup> `scrollHeight` gets the height of an element&#8217;s content including padding but **not** margins. Though `scrollHeight` is currently supported by all major browsers it is not part of a W3C recommendation so still considered proprietary. <sup><a href="http://developer.mozilla.org/en/DOM/element.scrollHeight">[2]</a></sup>

Now, some of you reading this might not like `scrollHeight` because it&#8217;s not a W3C recommendation. So for the interest of this group let&#8217;s explore an alternative solution.

Your first stab at the alternative to check whether we&#8217;re scrolled to bottom might look something like this:

<pre language="javascript">if ($('#box').scrollTop() == $('#box').outerHeight()) {
  // We're at the bottom.
}
</pre>

Novel, but that doesn&#8217;t work! `scrollTop` is quite an arbitrary value. In our case depending on which browser you choose the answer could be anything from 244px (Safari) to 289px (IE7). Clearly this is not a viable solution. 

To determine whether we&#8217;re truely at rock bottom we have to get the height of the element&#8217;s content and do a calculation based on that. Now we&#8217;re immediately faced with another problem &mdash; there is no sane way of determining the **actual** height of an element&#8217;s content because .outerHeight() always gives _300px_ plus padding as the answer. We could use an inner `div` to get over this problem:

<pre language="html">&lt;div id="box" style="height:300px; overflow:auto;"&gt;
  &lt;div class="inner"&gt;
    &lt;!-- Your content goes here --&gt;
  &lt;/div&gt;
&lt;/div&gt;
</pre>

So now we have a way of determining content height we can scroll to bottom:

<pre language="javascript">$('#box').animate({scrollTop: $('#box &gt; .inner').outerHeight()});
</pre>

And to check whether we&#8217;re scrolled to bottom we use the `offset` method:

<pre language="javascript">var elem = $('#box');
var inner = $('#box &gt; .inner');
if ( Math.abs(inner.offset().top) + elem.height() + elem.offset().top &gt;= inner.outerHeight() ) {
  // We're at the bottom!
}
</pre>

Not as striaght forward as `scrollHeight` aye?

Here&#8217;s a [test page](http://yelotofu.com/labs/jquery/test/scrollbottom.html) encompassing the stuff talked about in this article.

References:  
[1] [scrollHeight Property](http://msdn.microsoft.com/en-us/library/ms534615(VS.85).aspx)  
[2] [element.scrollHeight](http://developer.mozilla.org/en/DOM/element.scrollHeight)