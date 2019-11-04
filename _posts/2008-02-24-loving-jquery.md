---
id: 75
title: Loving jQuery
date: 2008-02-24T04:43:52+00:00
author: caphun
layout: post
guid: http://yelotofu.com/2008/02/loving-jquery/
permalink: /2008/02/loving-jquery/
dsq_thread_id:
  - "1241914786"
dsq_needs_sync:
  - "1"
categories:
  - JavaScript
tags:
  - JavaScript
  - jQuery
  - plugins
---
In recent weeks I have come to love [jQuery](http://jquery.com/). jQuery is this lightweight, elegant and so-much-fun-to-code-with JavaScript library. You may already have it in your source code if you&#8217;re using either the latest version of WordPress or Drupal.

jQuery is so easy to get to grips with, [the documentation](http://docs.jquery.com/Main_Page) is simple to follow and complete with loads of code samples.

jQuery&#8217;s elegance comes in the form of its ability to select DOM nodes through CSS-like syntax (i.e., CSS queries) in a compact way—brilliant for those who are already very familiar with CSS!

Most or even all actions start with a CSS query, which in a sense promotes the use of unobtrusive JavaScript as it&#8217;s simply easier to use the `$()` syntax than add a function directly into HTML.

jQuery is also very much down to earth in a practical way providing a few neat toggle functions:

  * [toggle](http://docs.jquery.com/Effects/toggle) — show/hide selected elements
  * [slideToggle](http://docs.jquery.com/Effects/slideToggle) — show/hide selected elements with slide Up/Down effects
  * [toggleClass](http://docs.jquery.com/Attributes/toggleClass) — add/remove a class from selected elements

There are also some handy plugins such as the [Flash plugin](http://jquery.lukelutman.com/plugins/flash/) and the [ifixpng plugin](http://jquery.khurshid.com/ifixpng.php), which fixes PNG transparency for `img` elements and CSS backgrounds in IE.5 and IE6.

If something isn&#8217;t built-in, extending jQuery is ridiculously easy via custom plugins. Here&#8217;s one way you could define a custom plugin:

<pre language="javascript">jQuery.fn.myPlugin = function() {
    // Your plugin code goes in here
}
</pre>

To take advantage of jQuery&#8217;s [chainability](http://docs.jquery.com/How_jQuery_Works#Chainability_.28The_Magic_of_jQuery.29) you need only add a single line returning the current context object—`this`:

<pre language="javascript">jQuery.fn.myPlugin = function() {
    // Your plugin code goes in here
    return this;
}
</pre>

To demonstrate how easy jQuery is to extend I created a simple one line plugin to toggle fadeIn and fadeOut effects, see below.

jQuery fadeToggle plugin:

<pre language="javascript">jQuery.fn.fadeToggle = function(s, fn){
    return (this.is(":visible"))
        ? this.fadeOut(s, fn)
        : this.fadeIn(s, fn);
};
</pre>

Example usage:

<pre language="javascript">jQuery(function($){
    $(".toggler").click(function(){
        $(".content").fadeToggle();
    });
});
</pre>

[A demo of jQuery fadeToggle plugin in action](/labs/fade-toggle/index.html)