---
id: 579
title: 'Tip: getting values from an options list'
date: 2009-10-22T03:16:56+00:00
author: caphun
layout: post
guid: http://yelotofu.com/?p=579
permalink: /2009/10/tip-getting-values-from-an-options-list/
oc_metadata:
  - |
    {		version:'1.1',		tags: {'jquery': {"text":"jquery","slug":"jquery","source":null,"bucketName":"current","bucketPlacement":"auto","_className":"Tag"}, 'javascript': {"text":"javascript","slug":"javascript","source":null,"bucketName":"current","bucketPlacement":"auto","_className":"Tag"}, 'optionslist': {"text":"optionslist","slug":"optionslist","source":null,"bucketName":"current","bucketPlacement":"auto","_className":"Tag"}, 'array': {"text":"array","slug":"array","source":null,"bucketName":"current","bucketPlacement":"auto","_className":"Tag"}, 'jquerymap': {"text":"jquerymap","slug":"jquerymap","source":null,"bucketName":"current","bucketPlacement":"auto","_className":"Tag"}}	}
oc_commit_id:
  - http://yelotofu.com/2009/10/tip-getting-values-from-an-options-list/1256152627
dsq_thread_id:
  - "1241829201"
dsq_needs_sync:
  - "1"
categories:
  - JavaScript
tags:
  - array
  - JavaScript
  - jQuery
  - jquerymap
  - optionslist
---
So, if you&#8217;ve ever converted an options list into a single array of values you might have intuitively done this:

<pre language="javascript">var select = $('#mySelectElement')[0];
var values = new Array();
for (var i=0; i &lt; select.length; i++) {
  values.push(select.options[i].value);
}
</pre>

Pretty boring aye? 

There is a snazzier (is that a word?) alternative, which is to use jQuery.map:

<pre language="javascript">var select = $('#mySelectElement')[0];
var values = $.map(select.options, function(n) { 
    return n.value; 
});
</pre>

OK, only one line saving but doesn&#8217;t that feel good?!?