---
id: 44
title: Clean URLs with CakePHP and IIS
date: 2007-08-04T20:04:45+00:00
author: caphun
layout: post
guid: http://yelotofu.com/2007/08/clean-urls-with-cakephp-and-iis/
permalink: /2007/08/clean-urls-with-cakephp-and-iis/
categories:
  - PHP
tags:
  - cakephp
  - clean url
  - iis
  - url rewrite
---
CakePHP works on IIS out of the box but it&#8217;s a pity the default setting is on querystring URLs. To serve clean URLs in CakePHP simply uncomment the following line in _/app/config/core.php_:

<pre lang="php">define ('BASE_URL', env('SCRIPT_NAME'));</pre>

By doing this CakePHP will direct each page request to the base script (by default thats _index.php_) and take charge of URL rewriting using the PATH_INFO environment variable.

This is ideal for serving CakePHP on IIS especially if you&#8217;re not using [Helicon Tech&#8217;s ISAPI Rewrite](http://www.isapirewrite.com/) and do not wish to fiddle about with configuring it or you&#8217;re on a shared environment and cannot touch the IIS settings.

Your CakePHP URLs will now look like:

http://mywebsite.com/index.php/posts/view/10

Rather than:

http://mywebsite.com/index.php?url=posts/view/10