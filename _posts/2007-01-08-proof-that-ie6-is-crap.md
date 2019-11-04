---
id: 841
title: Proof that IE6 is crap
date: 2007-01-08T19:01:11+00:00
author: caphun
layout: post
guid: http://yelotofu.com/2007/01/prof-that-ie6-is-crap/
permalink: /2007/01/proof-that-ie6-is-crap/
dsq_thread_id:
  - "1247342716"
dsq_needs_sync:
  - "1"
categories:
  - Browser Testing
  - CSS
tags:
  - bugfix
  - CSS
  - ie6
---
I have more than often had to fire-up IE6 out from the &#8220;un-loved&#8221; software repository to get kicked right back in the face with weird CSS bugs. I believe those reading this must be aware of at least one CSS quirk in the IE6 browser. For example, the PNG Alpha Transparency bug, fixed by Microsoft&#8217;s proprietary AlphaImageLoader or the strangely named Peek-a-boo bug requiring a position relative on the buggy floated element. These are just two out of what must be endless lists of problems. At the top of the annoyance list though must be the IE6 Background Flicker bug. When viewing a site using background images as hover/un-hover states IE6 will re-load a fresh image every event change on that element. The effect is a brief flicker on hover. By the way, this happens locally too but it&#8217;s too quick for the naked eye to notice. Firefox, Safari, Opera, Flock and probably any other browser on the planet does not have this problem! Worst still the fix is so simple, you wonder why the problem existed in the first place.To fix the IE6 Background Flicker bug use the document.execCommand method. In your CSS file add the following:

<pre>html {
  filter:expression(
    document.execCommand("BackgroundImageCache", false, true)
  );
}</pre>

Yes, it&#8217;s that simple! I found this fix at [Ajaxian.com](http://ajaxian.com/archives/no-more-ie6-background-flicker/trackback/). You&#8217;d probably want to implement some sort of sniffer to wrap around this fix. I used an IE conditional which serves the purpose nicely. For more solutions refer to the Ajaxian link above. Believe it or not, before finding this fix I looked into image caching, server cache control, CSS trickery and smashing the keyboard!

Lastly, apologies if anyone is offended by the title of this post. I&#8217;m venting my frustration after wasting many hours fixing perfectly valid CSS to cater for silly IE6 bugs.