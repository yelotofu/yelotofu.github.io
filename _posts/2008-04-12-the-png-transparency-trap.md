---
id: 85
title: The PNG Transparency Trap
date: 2008-04-12T15:23:12+00:00
author: caphun
layout: post
guid: http://yelotofu.com/?p=85
permalink: /2008/04/the-png-transparency-trap/
dsq_thread_id:
  - "1265786816"
dsq_needs_sync:
  - "1"
categories:
  - CSS
  - Reviews
  - Web Standards
tags:
  - ajaxian
  - alphaimageloader
  - ie6
  - iepngfix
  - pathfinder
  - png32
  - png8
---
Yesterday&#8217;s featured tutorial on [Ajaxian.com](http://ajaxian.com) was titled: [Hacking transparent PNG support into IE6 with IE PNG Fix, CSS and jQuery](http://ajaxian.com/archives/ajaxian-featured-tutorial-hacking-transparent-png-support-into-ie6-with-ie-png-fix-css-and-jquery) by Brian Dillard.

I wonder how this tutorial got onto Ajaxian as the topic is so much out of date. Ajaxian has always been a place of inspiration and a pit stop for the latest and greatest in the world of JavaScript and the whole Web scene. I was a little put off by this tutorial, though out of curiosity took a dive in anyway. 

The title alone is a mouthful to say the least and a glimpse of the trauma you will go through if you make the effort to read through the two part series. The tutorial specifically deals with how Pathfinder implemented transparent rounded corners on their new website. I know, nothing new. However, the worst is yet to come&#8230;

The transparent corners on [Pathfinder&#8217;s website](http://pathf.com) are actually background PNG32 images. IE6 doesn&#8217;t support PNG32 transparency so [IE PNG Fix](http://www.twinhelix.com/css/iepngfix/) came to the rescue. What IE PNG Fix does is it finds all PNGs contained within `img` tags and backgrounds, and adds some additional styles on-the-fly to present those PNGs via the `progid:DXImageTransform.Microsoft.AlphaImageLoader` filter. Then to overcome yet another limitation introduced by `AlphaImageLoader`, jQuery was used to append an `img` tag on-the-fly below the rounded box to form the bottom corners.

OK, it does the job so why whine about it? Well it&#8217;s an overkill if you think about it. Firstly IE6 has a problem with garbage collection when it comes to CSS filters. So the more `AlphaImageLoader` PNGs you have on a page the more unrecoverable memory you snatch away from your IE6 users. Secondly jQuery and IE PNG Fix are used in twine to tackle a single superfluous design problem, which adds a lot of unnecessary bloat. Pathfinder have truly fallen into the PNG transparency trap!

In the spirit of progress enhancement, which they avidly promote, they should have ignored IE6 and gave those users square boxes! However, for this particular case we&#8217;re in luck as there is an alternative&mdash;convert those dreaded PNG32s into transparent PNG8s!

To demonstrate proof of concept take a look at this screenshot below. On the left is Firefox, on the right is IE6:

<img src="http://yelotofu.com/wp-content/uploads/2008/04/png8_firefox_ie6_comparison.png" alt="Comparing PNG8 in Firefox and IE6" title="png8_firefox_ie6_comparison" width="300" height="300" class="aligncenter size-full wp-image-86" /> 

Not much difference aye? Apart from the aliased edges, which to be honest isn&#8217;t all that bad, they look pretty similar. I don&#8217;t think jagged edge corners are a sign of an amateur at work. I think it&#8217;s a reasonable sacrifice. By using PNG8 your corners won&#8217;t degrade as beautifully but they will degrade flawlessly. No hackery, less bloat; thereby saving memory, bandwidth and money.

Finally, I&#8217;m not suggesting we convert all our transparent PNGs into PNG8 format. I&#8217;m really just questioning whether the solution Pathfinder is presenting is the best solution and whether Ajaxian should be promoting it as it will no doubt lead many astray and fall into the PNG transparency trap.

Here are two very good SitePoint articles on how to make the most of PNG8 transparency in IE6:

  * [PNG8 &#8211; The Clear Winner](http://www.sitepoint.com/blogs/2007/09/18/png8-the-clear-winner/)
  * [Making &lsquo;IE6-friendly&rsquo; PNG8 Images]()

**Update 2008-06-17:** Interesting&#8230; [Transparent PNGs can even deadlock IE6!](http://blogs.cozi.com/tech/2008/03/transparent-png.html) Yet another reason to avoid this kind of hackery if you can!