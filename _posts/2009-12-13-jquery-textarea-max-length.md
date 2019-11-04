---
id: 597
title: 'jQuery: Textarea maxlength'
date: 2009-12-13T18:00:38+00:00
author: caphun
layout: post
guid: http://yelotofu.com/?p=597
permalink: /2009/12/jquery-textarea-max-length/
oc_metadata:
  - |
    {		version:'1.1',		tags: {'html-5': {"text":"HTML 5","slug":"html-5","source":{"_className":"SocialTag","url":"http://d.opencalais.com/dochash-1/20d3d936-f5a3-3a25-9cd8-ad052848c608/SocialTag/5","subjectURL":null,"type":{"_className":"ArtifactType","url":"http://s.opencalais.com/1/type/tag/SocialTag","name":"SocialTag"},"name":"HTML 5","makeMeATag":true,"importance":1,"normalizedRelevance":1},"bucketName":"current","bucketPlacement":"auto","_className":"Tag"}, 'textarea': {"text":"textarea","slug":"textarea","source":null,"bucketName":"current","bucketPlacement":"auto","_className":"Tag"}, 'maxlength': {"text":"maxlength","slug":"maxlength","source":null,"bucketName":"current","bucketPlacement":"auto","_className":"Tag"}, 'html5': {"text":"html5","slug":"html5","source":null,"bucketName":"current","bucketPlacement":"auto","_className":"Tag"}, 'html': {"text":"html","slug":"html","source":null,"bucketName":"current","bucketPlacement":"auto","_className":"Tag"}, 'jquery': {"text":"jquery","slug":"jquery","source":null,"bucketName":"current","bucketPlacement":"auto","_className":"Tag"}}	}
oc_commit_id:
  - http://yelotofu.com/2009/12/jquery-textarea-max-length/1260698449
dsq_thread_id:
  - "1241779491"
dsq_needs_sync:
  - "1"
categories:
  - JavaScript
tags:
  - html
  - HTML 5
  - html5
  - jQuery
  - maxlength
  - textarea
---
Being able to restrict the maximum length of user input from the interface directly is very convenient and practical in use. We do this a lot with `input` elements. Unfortunately `textarea` elements do not natively support the `maxlength` attribute. This attribute was finally added in HTML5 but at the time of writing Chrome is the only browser supporting it.

Naturally many have used JavaScript to rectify this problem and I&#8217;d be doing the same here. The difference is we won&#8217;t be putting anything special in the markup but will simply use the `maxlength` attribute within our `textarea` as if it&#8217;s native &mdash; like so:

**HTML**

<pre language="html">&lt;textarea cols="30" rows="5" maxlength="10"&gt;&lt;/textarea&gt;
</pre>

This is looking good for HTML5 compatibility. And here&#8217;s the magic:

**jQuery** 

<pre language="javascript">jQuery(function($) {

  // ignore these keys
  var ignore = [8,9,13,33,34,35,36,37,38,39,40,46];

  // use keypress instead of keydown as that's the only 
  // place keystrokes could be canceled in Opera
  var eventName = 'keypress';

  // handle textareas with maxlength attribute
  $('textarea[maxlength]')

    // this is where the magic happens
    .live(eventName, function(event) {
      var self = $(this),
          maxlength = self.attr('maxlength'),
          code = $.data(this, 'keycode');

      // check if maxlength has a value.
      // The value must be greater than 0
      if (maxlength && maxlength &gt; 0) {

        // continue with this keystroke if maxlength
        // not reached or one of the ignored keys were pressed.
        return ( self.val().length &lt; maxlength
                 || $.inArray(code, ignore) !== -1 );

      }
    })

    // store keyCode from keydown event for later use
    .live('keydown', function(event) {
      $.data(this, 'keycode', event.keyCode || event.which);
    });

});
</pre>

See [live example.](http://yelotofu.com/labs/jquery/snippets/textarea/index.html)

This code could probably be enhanced further by triggering custom events when the maximum length is reached or include a character counter of some sort within the keypress handler. Your imagination is the limit!