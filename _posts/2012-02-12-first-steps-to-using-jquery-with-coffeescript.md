---
id: 792
title: First steps to using jQuery with CoffeeScript
date: 2012-02-12T01:52:35+00:00
author: caphun
layout: post
guid: http://www.yelotofu.com/?p=792
permalink: /2012/02/first-steps-to-using-jquery-with-coffeescript/
categories:
  - JavaScript
  - jQuery
tags:
  - coffeescript
  - firststeps
  - jQuery
---
A colleague recently asked me how you typically write the jQuery DomReady and closure syntaxes with <a href="http://coffeescript.org/" target="_blank">CoffeeScript</a>. It&#8217;s actually quite simple but did require a bit of fiddling around to find the right recipe. So I thought I&#8217;d share this with you all just in case you&#8217;re wondering too!

#### DomReady:

<pre># CoffeeScript
jQuery ($) -&gt;
  # your code here!

// JavaScript
jQuery(function($) {
  // your code here!
});
</pre>

#### DomReady v2:

<pre># CoffeeScript
$(document).ready -&gt;
  # your code here!

// JavaScript
$(document).ready(function() {
  // your code here!
});
</pre>

#### Passing jQuery into a closure:

<pre># CoffeeScript
(($) -&gt;
  # your code here!
) jQuery

// JavaScript
(function($) {
  // your code here!
})(jQuery);
</pre>

#### Bonus: Ternary statements

<pre># CoffeeScript
a = if found then b else c

// JavaScript
a = found ? b : c;
</pre>

Do you have a recipe for this too? What is it?