---
id: 29
title: What are Microformats?
date: 2007-03-15T04:03:28+00:00
author: caphun
layout: post
guid: http://yelotofu.com/2007/03/what-are-microformats/
permalink: /2007/03/what-are-microformats/
categories:
  - Web Standards
tags:
  - hcard
  - microformats
  - semantic web
---
To start with, here&#8217;s my stab at a [Microformats](http://microformats.org) definition:_&#8220;Microformats are bits of code you add to your XHTML markup to define a piece of text and by doing so you make that bit of text semantic.&#8221;_

As you could see it doesn&#8217;t make much sense to the average punter. When I first looked into Microformats I noticed the apparent lack of good definitions. After further reading I could see why. Microformats are not easily defined in simple words due to the diversity of the concept, but in practise it&#8217;s very simple. Therefore the best way to teach someone Microformats is to show them some code.

Take a quick look at this simple Microformats [hCard](http://microformats.org/wiki/hcard):

<pre>&lt;div id="hcard-Ca-Phun-Ung" class="vcard"&gt;
  &lt;div class="fn"&gt;Ca Phun Ung&lt;/div&gt;
  &lt;div class="org"&gt;Yelotofu&lt;/div&gt;
  &lt;div class="email"&gt;harvest-me@yelotofu.com&lt;/div&gt;
  &lt;div class="adr"&gt;
    &lt;div class="street-address"&gt;X Street&lt;/div&gt;
    &lt;div class="country-name"&gt;Hong Kong&lt;/div&gt;
  &lt;/div&gt;
  &lt;div class="tel"&gt;+852 xxxx xxxx&lt;/div&gt;
&lt;/div&gt;</pre>

And the output looks like this

<pre>Ca Phun Ung
Yelotofu
harvest-me@yelotofu.com
X Street
Hong Kong
+852 xxxx xxxx</pre>

It doesn&#8217;t look like much on the surface but that&#8217;s the whole point, Microformats do not interfer with your sites layout or typography. In essence, it&#8217;s much like XML but because we&#8217;re dealing with XHTML, self-defined tags are not supported so the class attribute is used instead.

Microformats are an intriguing progression towards the [Semantic Web](http://www.w3.org/2001/sw/). This is an area I&#8217;m very much interested in so will continue to post my findings as I learn and progress along the Microformats highway. Stay tuned!