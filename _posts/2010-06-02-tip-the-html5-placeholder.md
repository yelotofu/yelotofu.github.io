---
id: 633
title: HTML5 Placeholders
date: 2010-06-02T02:47:46+00:00
author: caphun
layout: post
guid: http://yelotofu.com/?p=633
permalink: /2010/06/tip-the-html5-placeholder/
categories:
  - JavaScript
tags:
  - html5
  - JavaScript
  - jQuery
  - placeholder
  - placeholders
---
HTML5 adds a new attribute to most form elements called a [placeholder](http://dev.w3.org/html5/spec/Overview.html#the-placeholder-attribute). Its purpose is to add a short hint inside data entry points that disappear on focus. This type of interaction isn&#8217;t new but is new to HTML as of version 5. For this reason not all browsers have implemented this feature. Try it to see which of your browsers support the following bit of code!

**HTML**

<pre language="html">&lt;input type="text" placeholder="click me!"&gt;
</pre>

So now we have a problem. Some browsers support it and others don&#8217;t!? Foresee client issues? Not to worry, here&#8217;s a workaround using the latest jQuery 1.4 features!

**JavaScript**

<pre language="javascript">jQuery(document).ready(function($) {

  // first check if placeholder attribute is supported
  if ($('&lt;input/&gt;')
        .attr('placeholder','')[0]
        .placeholder === undefined) {

    // text input placeholder
    $('input[placeholder]')
      .each(function() { 
        this.value === ''
          ? this.value = $(this).attr('placeholder')
          : false; 
      })
      .live('focusin focusout', function(event) {
        event.type == 'focusout' && this.value === '' 
          ? this.value = $(this).attr('placeholder')
          : this.value === $(this).attr('placeholder')
            ? this.value = '' 
            : false;
      });

  }

});
</pre>

This is not a complete solution as there are other things to consider such as visual style and what happens when you submit the form. But I&#8217;ll let you mull over those.<img src="http://localhost:8888/wp-includes/images/smilies/icon_smile.gif" alt=":)" class="wp-smiley" /> 

Demo and code sample: <http://jsbin.com/ujosa/edit>