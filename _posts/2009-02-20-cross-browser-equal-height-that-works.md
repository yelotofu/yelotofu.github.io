---
id: 440
title: Cross browser equal height that works
date: 2009-02-20T15:24:29+00:00
author: caphun
layout: post
guid: http://yelotofu.com/?p=440
permalink: /2009/02/cross-browser-equal-height-that-works/
dsq_thread_id:
  - "1241858558"
dsq_needs_sync:
  - "1"
categories:
  - CSS
tags:
  - crossbrowser
  - CSS
  - equalheight
---
Since its dawn, CSS has been plagued with the lack of a bullet proof technic to produce equal height columns, boxes and grids. The fortunate few have been able to avoid this problem by &#8220;designing for the Web&#8221; — **no** crazy fonts; **no** equal height.

For those unfortunate millions, it isn&#8217;t so cut &#8216;n&#8217; dry. Many designers continue to create vertically aligned and beautifully designed mock-ups in PhotoShop fully expecting the end result to look the same on the Web (and quite rightly so); if not, at least the columns should remain at equal height in all scenarios!

Thankfully `display:table-cell` and `display:inline-block` come to the rescue. Like magic, these change the characteristics of any block level element in amazing ways giving elements table-cell like behaviour; The latter even allows proper element tiling in an orderly fashion. If you come from the hybrid-layout era you&#8217;d know how convenient tables for layout were. These two CSS properties give the best of both worlds &#8211; better markup semantics with grid-like features.

This sounds like fancy stuff but really, it is quite simple. Code always speaks louder than words so here&#8217;s an example to get the juices going: [Working with cells in CSS](http://yelotofu.com/labs/grid/equal-height-columns.html)

Now, let me take you through the code once you&#8217;ve had a gander through the source code&#8230;

<pre language="css">.grid { display: table; }
.grid li { display: table-cell; }
</pre>

These two lines are all we need to change a list into a table row. But here&#8217;s the catch — this only works in Mozilla, Opera and Safari browsers; as usual IE is the odd one out. The forthcoming IE8 will support these display values but for now we have to hack our way to a solution that really works. Here&#8217;s where things get interesting.

To get equal height in IE we turn to `inline-block`. IE has some buggy CSS support. `inline-block` only works in IE if we duplicate it with an `inline` call afterwards, like so:

<pre language="css">.grid {
  width: 100%;
  height: 1%;
}
.grid li {
  display: inline-block;
  vertical-align: top;
  height: 100%;
}
.grid li {
  display: inline;
  width: 24.9%;
}
</pre>

In the above we&#8217;re specifying a width of 24.9% — this value will be different depending on the number of cells in a row. Our example has four, so in theory it should be 25%. This weird value is just evidence how bad IE&#8217;s support is when it comes to CSS.

Finally to produce equal height columns we increase the bottom padding to a very high value to overcome the varying content height:

<pre language="css">/* equal column height hack - for IE6 &amp; IE7 only */
.grid {
  voice-family: ""}"";
  voice-family: inherit;
  overflow: hidden;
}
.grid li {
  voice-family: ""}"";
  voice-family: inherit;
  padding-bottom: 9999px;
  margin-bottom: -9999px;
}
</pre>

That&#8217;s it! Pretty simple if it wasn&#8217;t for IE!<img src="http://localhost:8888/wp-includes/images/smilies/icon_wink.gif" alt=";)" class="wp-smiley" /> 

Here are two more examples based on the concepts talked about in this article:

  * [Floatless layouts with display:table-cell](http://yelotofu.com/labs/grid/floatless-layout.html)
  * [Floatless layouts with display:inline-block](http://yelotofu.com/labs/grid/inline-block.html)

**Further reading:**

  * [Everything You know about CSS is wrong](http://www.digital-web.com/articles/everything_you_know_about_CSS_Is_wrong/)
  * [Cross Browser display:inline-block](http://www.ruzee.com/files/ib-fix/test.html)
  * [Equal Height boxes with CSS, part 2](http://www.456bereastreet.com/archive/200406/equal_height_boxes_with_css_part_ii/)

Go crazy!