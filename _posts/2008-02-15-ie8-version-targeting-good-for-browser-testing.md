---
id: 76
title: IE8 Version Targeting good for Browser Testing
date: 2008-02-15T02:16:17+00:00
author: caphun
layout: post
guid: http://yelotofu.com/2008/02/ie8-version-targeting-good-for-browser-testing/
permalink: /2008/02/ie8-version-targeting-good-for-browser-testing/
categories:
  - Web Standards
tags:
  - browsertesting
  - compatibility
  - ie8
  - versiontargeting
---
If this is the first you&#8217;ve heard of Microsoft&#8217;s proposed version targeting feature for IE8 I highly recommend doing some read up on it as this is destined to affect every internet professional in some way or another. Go read [Microsoft&#8217;s announcement](http://blogs.msdn.com/ie/archive/2008/01/21/compatibility-and-ie8.aspx), then these two ALA articles, [Beyond DOCTYPE](http://www.alistapart.com/articles/beyonddoctype) and it&#8217;s companion [&#8220;From Switches to Targets: A Standardista&#8217;s Journey&#8221;.](http://www.alistapart.com/articles/fromswitchestotargets)

Setting aside the [controversy and heated debates](http://www.maxdesign.com.au/2008/01/24/1e8/) of good vs evil, I think the benefit of the X-UA-COMPATIBLE meta tag could come in the form of browser testing. Freelance developers (like me) who do not have access to big testing budgets or a room full of computers with different versions of IE on every machine might find this a life saver. I currently have many standalone versions of IE on a single laptop for testing purposes. However these standalones are very buggy and do not always display exactly as a proper IE installation, let alone the initial pain of finding and installing each individual standalone. The possibility of using one IE installation, which updates itself on every new release, to test all versions of IE (from IE7 onwards that is) is very appealing. Even though the footprint of each new version will increase due to this backwards compatibility mode Microsoft will in time stop supporting older versions when they reach their life&#8217;s end, for software that&#8217;s typically 8 years.

Good as it were I have to agree with [Jeremy Keith](http://adactio.com/journal/) that it&#8217;s a [broken feature](http://adactio.com/journal/1403) simply because you cannot opt-out from it due to the renderer defaulting to IE7. Not including the meta tag means your site is sentenced to death on the IE7 renderer, which isn&#8217;t all that great in terms of standards compliance. It also goes against progressive enhancement which has become somewhat standard best practice now.

I do think this version targeting meta tag is a handy addition but Microsoft should also give us the ability to opt-out and not penalize us for not using this proprietary feature.