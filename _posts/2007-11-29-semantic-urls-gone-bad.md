---
id: 41
title: Semantic URLs gone bad!?!
date: 2007-11-29T15:58:09+00:00
author: caphun
layout: post
guid: http://yelotofu.com/2007/11/semantic-urls-gone-bad/
permalink: /2007/11/semantic-urls-gone-bad/
dsq_thread_id:
  - "1265786493"
categories:
  - Web Standards
tags:
  - friendlyurls
  - semantics
  - semanticurls
  - SEO
---
Semantic URLs, also known as Friendly URLs, are human readable URLs that would otherwise be a list of query string parameters with meaningless ID&#8217;s. Semantic URLs are a good thing but could it be too good to the point of turning bad?

I&#8217;ve been mulling over the use of Semantics in URLs for a while. How far could you go with the semantics until things turn upside down? Where does one strike the balance between Search Engines and Humans? Are we prone to a second wave of keyword stuffing? Search Engines love keywords but will website owners fall foul of keyword stuffing on the URL as was evident with the Keyword meta tag?

In a recent project I had the opportunity of voicing my opinion on the matter of URL structure. The website in context sells products with deep-linking categories of which some have multiple parent categories. I recommended the KISS (Keep It Simple, Stupid) approach, keeping URLs short and unique but the client was more concerned with SEO so wanted product URLs to have as much semantics as possible; if a particular category had multiple parents then all parent categories should display on the product URL to form a seemingly hierarchical structure. As you could imagine product URLs then start to look unwieldy. Take a look at this example URL structure:

<pre>/plants/_/shrubs/roses/shrub-rose/bush-rose/other-shrub-rose/rosa-queen-of-denmark/classid.77933/</pre>

What the heck is that? Is that still considered friendly? For starters it does not describe a proper hierarchy since &#8220;other-shrub-rose&#8221; is not a subcategory of &#8220;bush-rose&#8221; and &#8220;classid.77933&#8243; is not a subset of &#8220;rosa-queen-of-demark&#8221;; rather it&#8217;s product id. The URL should really look more like this:

<pre>/plants/shrubs/roses/77933-Rosa-Queen-Of-Denmark</pre>

or even

<pre>/plants/77933-Rosa-Queen-Of-Demark</pre>

Showing all parent categories when there are multiple routes defeats the idea of hierarchy. On top of that the site does not always have a page for each category. Category names can also be displayed in any order within the URL resulting in multiple URLs point to the same product page. Hence hierarchy isn&#8217;t even important though it&#8217;s shown to be with the URL structure. The product URLs are now far from friendly, in fact they are: ugly, wordy, overly deep-linked and look very bad in print.

In conclusion. Does all this really matter? Do site visitors notice URLs in the first place? Do search engines check whether a site is stuffing URLs with keywords? Is serving identical content to multiple URLs detrimental to a site? I&#8217;m no SEO expert so I&#8217;m afraid these will remain as questions. One thing I am certain of however is that building an SEO friendly site is about creating quality content, concentrating on document quality, using semantic markup and delivering an accessible site. In the end, it&#8217;s down to us as web professionals to make sure we do not take advantage of unset rules by exploiting what should be a good thing—Semantic URLs.

Further reading:

  * [Use Targeted Keywords in URL](http://www.webrankinfo.com/english/seo-news/keywords-in-url.php)
  * [SEO and URL structure](http://www.clickz.com/showPage.html?page=3622997)
  * [How to Make your URLs SEO Friendly](http://www.avangate.com/articles/url-rewriting_70.htm)