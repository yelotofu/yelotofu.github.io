---
id: 98
title: 'jQuery: Shuffle Plugin'
date: 2008-08-29T03:28:55+00:00
author: caphun
layout: post
guid: http://yelotofu.com/?p=98
permalink: /2008/08/jquery-shuffle-plugin/
dsq_thread_id:
  - "1241884147"
dsq_needs_sync:
  - "1"
categories:
  - Labs
tags:
  - array
  - JavaScript
  - jQuery
  - plugin
  - shuffle
---
I recently came across a really compact [array shuffling](http://jsfromhell.com/array/shuffle) function on [JSFromHell.com](http://jsfromhell.com), which I thought would make a nifty jQuery plugin. 

This jQuery shuffle plugin could be applied to any HTML element or Array object.

<pre language="javascript">(function($){
  $.fn.shuffle = function() {
    return this.each(function(){
      var items = $(this).children();
      return (items.length) 
        ? $(this).html($.shuffle(items)) 
        : this;
    });
  }
	
  $.shuffle = function(arr) {
    for(
      var j, x, i = arr.length; i; 
      j = parseInt(Math.random() * i), 
      x = arr[--i], arr[i] = arr[j], arr[j] = x
    );
    return arr;
  }	
})(jQuery);
</pre>

_Due to line wrapping issues in this post I inserted a few hard carriage returns in the above snippet (sorry)._

Example 1: shuffle an unordered list

<pre language="javascript">$('ul').shuffle();
</pre>

Example 2: shuffle an array

<pre language="javascript">var arr = [1,2,3,4,5,6];
arr = $.shuffle(arr);
</pre>

There is a [demo here](http://yelotofu.com/labs/jquery/snippets/shuffle/demo.html). And for those interested I encourage you to [download the plugin](http://yelotofu.com/labs/jquery/snippets/shuffle/jquery.shuffle.js) for closer inspection.