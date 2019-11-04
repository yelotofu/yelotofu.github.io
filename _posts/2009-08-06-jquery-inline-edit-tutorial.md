---
id: 469
title: jQuery Inline Edit tutorial
date: 2009-08-06T06:04:41+00:00
author: caphun
layout: post
guid: http://yelotofu.com/?p=469
permalink: /2009/08/jquery-inline-edit-tutorial/
oc_commit_id:
  - http://yelotofu.com/2009/08/jquery-inline-edit-tutorial/1255879204
oc_metadata:
  - |
    {		version:'1.1',		tags: {'editinplace': {"text":"editinplace","slug":"editinplace","source":null,"bucketName":"current","bucketPlacement":"auto","_className":"Tag"}, 'inlineedit': {"text":"inlineedit","slug":"inlineedit","source":null,"bucketName":"current","bucketPlacement":"auto","_className":"Tag"}, 'inplaceedit': {"text":"inplaceedit","slug":"inplaceedit","source":null,"bucketName":"current","bucketPlacement":"auto","_className":"Tag"}, 'javascript': {"text":"JavaScript","slug":"javascript","source":null,"bucketName":"current","bucketPlacement":"auto","_className":"Tag"}, 'jquery': {"text":"jquery","slug":"jquery","source":null,"bucketName":"current","bucketPlacement":"auto","_className":"Tag"}, 'plugin': {"text":"plugin","slug":"plugin","source":null,"bucketName":"current","bucketPlacement":"auto","_className":"Tag"}}	}
dsq_thread_id:
  - "1241842415"
dsq_needs_sync:
  - "1"
categories:
  - JavaScript
tags:
  - editinplace
  - inlineedit
  - inplaceedit
  - JavaScript
  - jQuery
  - plugin
---
<small><a href="http://www.webhostinghub.com/support/es/misc/El+concepto" rel="nofollow" target="_blank">Spanish translation</a> by Maria Ramos.</small>

A friend recently asked me to review his edit-in-place code which turned out to be a modification of the one found at <a href="http://docs.jquery.com/Tutorials:Edit_in_Place_with_Ajax" target="_blank">http://docs.jquery.com/Tutorials:Edit_in_Place_with_Ajax</a>. Reading the tutorial on that page I asked myself how I would do this differently? Defining a global `setClickable()` function and then calling `$('#editInPlace").click()` is totally uncool, essentially limiting yourself to one edit-in-place area per page.

Since the concept of edit-in-place is so simple and the implementation should be likewise I want to try and tackle this as a tutorial by going through concepts and teaching to build from scratch.

## The concept

There&#8217;s a piece of text on a page, e.g. a heading or paragraph, looking plain and un-interesting. When you hover over it however a visual highlight, usually pale yellow, indicates that it&#8217;s something special &#8211; an editable region. You then click on the text and it magically transforms into an editable box with save and cancel buttons tagged at the end. On clicking either save or cancel the editable box transforms back into its original form with text updated if saved.

## The build

What we want to do is put these concepts into code whilst building something that&#8217;s re-usable. A plugin will do the trick! Let&#8217;s call our plugin inlineEdit.

We are only 3 steps away from achieving our goal! Follow along&#8230;

### Step 1: Getting the basics right

The basic functionality consists of a static text element (`span`, `div` etc&#8230;) that can transforms into an `input` element on click. And on hover the text element will highlight to indicate special interactions.

Here&#8217;s our first pass: [Basic Interaction](http://yelotofu.com/labs/jquery/snippets/inlineEdit/demo_basics.html) 

**Code explanation:** Our plugin accepts a CSS class name defined in a stylesheet which is used to toggle the text element&#8217;s classname &#8211; a class defining a background-color typically #ffC is sufficient for this. On clicking we replace the entire contents of the original text element with an `input` element and pass the original content into the `input` as its value. For now changes are saved when the `input` loses focus.

### Step 2: Save, Cancel & Callbacks

As you may notice above we saved on blur and there is no way of canceling changes. Let&#8217;s improve the interaction by adding a save button. This is important as you&#8217;d want to do something with the changes or allow a user to manually cancel. Every application does something different at the saving stage so we&#8217;ll simply define a save callback and let the implementer decide what to do on save, be it Ajax post or what not. The save action is also cancelable by returning false inside the callback.

Here is our second pass: [Save, cancel and callbacks](http://yelotofu.com/labs/jquery/snippets/inlineEdit/demo_callbacks.html) 

### Step 3: Finishing Off

Our plugin is nearly there. Just a few nice finishing touches remaining. We want to give the user ability to change the button label and pass an initial value. Also to make the plugin more re-usable we want to move the core plugin code out to a separate file and reference it instead. To set the stage for further improvements in the future we also split the code into two distinct clauses.

Final result: [Live Demo](http://yelotofu.com/labs/jquery/snippets/inlineEdit/demo_final.html) and <a href="http://github.com/caphun/jquery.inlineedit" target="_blank">source code is here</a>

## Usage

Now to use this brand spanking new plugin we simply apply it to any DOM element like so:

HTML

<pre language="html">&lt;span class="editable"&gt;Hello World!&lt;/span&gt;
</pre>

JavaScript &#8211; Basic

<pre language="javascript">$(function() {
  $('.editable').inlineEdit();
});
</pre>

JavaScript &#8211; Customised button label with save callback

<pre language="javascript">$(function() {
  $('.editable').inlineEdit({
    buttonText: 'Add',
    save: function(e, data) {
      return confirm('Change name to '+ data.value +'?');
    }
  });
});
</pre>

**Feedback welcome** &#8211; if you happen to improve upon this code base please share-a-like! 

Enjoy!

**Update 26-Aug-09:** Added placeholder for cases when text is empty; changed label option to buttonText to minimise confusion.

**Update 18-Oct-09** Fixed bug in setting initial value via script.

**Update 17-Jan-10** Moved code to <http://github.com/caphun/jquery.inlineedit>. I will continue to improve this plugin from there. Feel free to fork it!