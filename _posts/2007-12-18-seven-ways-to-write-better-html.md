---
id: 57
title: '7 Ways To Write &#8220;Better&#8221; HTML'
date: 2007-12-18T17:26:42+00:00
author: caphun
layout: post
guid: http://yelotofu.com/2007/12/7-ways-to-better-html/
permalink: /2007/12/seven-ways-to-write-better-html/
dsq_thread_id:
  - "1250072537"
dsq_needs_sync:
  - "1"
categories:
  - Accessibility
  - Web Standards
tags:
  - Accessibility
  - barcamphongkong2007
  - CSS
  - html
  - presentation
  - semantics
  - SEO
  - webstandards
---
BarCamp came and went, I&#8217;m still experiencing the aftermath; making new connections on [Facebook](http://www.facebook.com) daily and checking the [BarCamp Hong Kong 2007 Flickr Group](http://www.flickr.com/groups/barcamphongkong2007/) constantly for new photos! Anyway, It&#8217;s about time I catalogued my talk before it&#8217;s too late! [The original presentation slide show](http://yelotofu.com/presentations/barcamphk2007/) was created with [S5](http://meyerweb.com/eric/tools/s5/) (a standards compliant and accessible slide show system). Feel free to run that side-by-side whilst reading this article as it&#8217;s segmented to match the presentation. **Warning:** This post is pretty long! I hope I don&#8217;t bore you.

## Introduction

HTML is an age old topic which I&#8217;m sure you&#8217;re already very familiar with and has been talked about zillions of times. However, I think there is room for such a topic given the apparent lack of knowledge of Web Standards among the general web populous in Hong Kong. Hopefully by the end of this post I will of at least spark some interest in writing better, and by better I mean, semantically rich and standards compliant HTML.

## 1. Use a DOCTYPE declaration

If you&#8217;re using a HTML editor to create HTML then chances are a DOCTYPE is added to your pages automatically, so generally we tend to not take much notice of it. There are several DOCTYPE flavours however. A Strict DTD is used when you want clean markup free from presentational elements. A Transitional DTD when you want to add some presentational features to your HTML. There is also a Frameset DTD used for laying out pages with framesets, however you should never need this one; you shouldn&#8217;t be using frames!

It&#8217;s always good practice to add a DOCTYPE to the top of each and every HTML page because it enables what we call DOCTYPE switching. There are essentially two basic modes “quirks mode” and “standards mode”. In quirks mode the browser will behave like old browsers of the late 90&#8242;s and standards mode will follow the W3C recommendations. A browser will work in quirks mode if there is no DOCTYPE to be found. Internet Explorer will even switch to quirks mode if the first line of your HTML has no DOCTYPE, a blank line counts too! The most famous effect of switching to “standards mode” is the change in [the Box model and problems with the old IE model](http://www.communitymx.com/content/article.cfm?cid=E0989953B6F20B41). There is also a third &#8220;almost-standards mode&#8221; which is available in Mozilla and Firefox browsers. The almost-standards mode is activated by a transitional DTD and doesn&#8217;t follow the W3C cell height specification. So next time you create a new HTML file give yourself a second to think about the DOCTYPE you&#8217;re using.

OK, which DOCTYPE should you use? It depends on the situation. [Jeffrey Zelman](http://www.zeldman.com/) wrote a great article to help [Fix Your Site With the Right DOCTYPE](http://www.alistapart.com/articles/doctype/) and [Henri Sivonen](http://hsivonen.iki.fi/author/) wrote in detail about [Activating the right layout mode using the DOCTYPE](http://hsivonen.iki.fi/doctype/). Generally, if you&#8217;re starting out on a new project with a blank canvas I&#8217;d recommend using a strict DTD which helps to facilitate adherence to standards, obviously make the effort to [validate](http://validator.w3.org) as well to **ensure** compliance!

## 2. Don&#8217;t Abuse the Good!

HTML is very simple to learn. In fact it&#8217;s so easy anyone could pretty much pick it up, as well as be proficient, in about 3 days. For that reason it&#8217;s a “language” that&#8217;s prone to exploitation as most learn from bad examples. There are only a handful of tags and only 30 are frequently used. The most exploited of them all are the `table` and `blockquote` elements.

The biggest step to writing better markup is to [throw away your tables](http://www.stopdesign.com/articles/throwing_tables/), but not all of them, only those being used for layout purposes. Think of tables as “data tables” and you&#8217;re on the right track. This is something that could prove difficult for those used to creating tables for layout. I myself started building websites in the era of table dominance and found it difficult to switch at first. I know how difficult it could be to unlearn bad habits, but believe me you will benefit immensely and it will open many doors. I would never go back to tables for layout now that I&#8217;ve mastered CSS layouts. Still not convinced? Pop open a new browser and read this interestingly animated article by Merikallio & Pratt on [Why tables for layout is stupid](http://www.hotdesign.com/seybold/).``

By definition a `blockquote` is _a BLOCK of QUOTEs_, hence a `blockquote` should always start with a `p`, but `blockquote` elements are often mis-used as indenter&#8217;s. Example of the write way to use a `blockquote`:  
[sourcecode language="html"]  
<p><cite>Eric Meyer</cite> wrote:</p>  
<blockquote cite="http://meyerweb.com/eric/thoughts/2005/03/11/social-protocols/">  
<p>What&#8217;s so interesting to me is that the guys who  
decided tofocus on the positive went out and did something;  
those who want to mix in the negative seem to have  
nothing to offer except complaints.</p>  
</blockquote>  
<p>An excellent contrast between those who want to  
build new things and those who want to tear them down.</p>  
[/sourcecode]  
Example taken from <cite><a href="http://tantek.com/presentations/2005/09/elements-of-xhtml/">The Elements of Meaningful XHTML</a></cite> by <cite><a href="http://www.tantek.com/">Tantek Çelik</a></cite>

## 3. Use the Right Tag for the Right Job

Like a carpenter won&#8217;t use his screwdriver to hammer a nail into a piece of wood so the `p` element should not be used to break a line! However WYSIWYG editors tend to exploit the `p` element by using it as a line-break rather than a wrapper for a paragraph of text. Don&#8217;t do this in your hand crafted master piece!

There are 6 heading levels (`h1`, `h2`, `h3`, `h4`, `h5`, `h6`) – `h1` being most important, and `h6` least important. Headings are used to section a page into logical chunks.

The `em` element is used to give a word or sentence emphasis, it does not mean italic text even though that&#8217;s what it looks like in a browser. Again WYSIWYG editors often exploit this fact, by producing an `em` element when users click on the _I_ icon.

The `strong` element is also in a similar situation being mistaken as _bold text_. The `strong` element should only be used when a stronger emphasis than the `em` element is needed. And `em`&#8216;s can be nested to give further emphasis.

Lastly there is `ul`, `ol`, and `dl`. Only use the `ol` when you have a list of items in which changing the order of an item will change the meaning of that list. A `ul` is for general lists and `dl` elements could be used for definitions or key-value pairs.

## 4. Avoid Bed and BReakfast markup

[<b>ed and <br>eakfast markup](http://tantek.com/log/2002/10.html#L20021022t1432) is a term coined by [Tantek Çelik](http://www.tantek.com/) to describe the way people mis-use `b` and `br` elements for headings and paragraphs respectively. B & BR is bad practice because it adds presentational markup and takes away what could have been an opportunity for more semantic meaning in a piece of text. [See presentation slide 18-20 for example.](http://yelotofu.com/presentations/barcamphk2007/)

## 5. Headings are important

As previously mentioned there are six heading levels. Where you start the first `h1` element is crucial to the overall structure and accessibility of a page. It&#8217;s usually best to have one `h1` only and that&#8217;s usually the site name. However, if you have a page of article listings (like a blog home page) then you might decide that the title of each article is far more important than the site name, hence it&#8217;s also possible to use `h1` elements as the title of each article. In which case you will end up with multiple `h1` elements. It&#8217;s also important not to skip levels in the page structure as it will mess up page quality. Sectioning a page into meaningful headings will also aid some screen readers and browsers to quickly navigate the page content by jumping from heading to heading. Finally headings are good for SEO, Accessibility and much better than `div` or `span` elements. A word of advice is to use headings where ever it makes sense and keep meaningless markup to a minimum.

### 6. Don&#8217;t forget ALT text!

_Bad:_ `<img src=”car_photo.jpg”>`  
**Acceptable:** `<img src=”car_photo.jpg” alt=””>`  
_**Good:**_ `<img src=”car_photo.jpg” alt=”my dream car”>`

It is a basic requirement of the WAI Level 1 guidelines that all `img` elements should have an accompanying ALT text. Now there may not seem any point there but what if your image is a link to another section of the site? An image link for example:

**Bad example:**  
[sourcecode language="html"]  
<a href="portfolio.html"><img src="screenshot.jpg" /></a>  
[/sourcecode]  
Users who navigate your site with images turned off or use screen readers will not be able to make sense of the above. Worse still are images used as the main navigation without an ALT text for people to follow. An ALT text should be descriptive and give the user an idea of the context of the image. Sometimes it means explaining visual aspects; sometimes it&#8217;s a case of spelling out embedded copy. Make an effort to remove any decorative images from HTML and place inside CSS. If a decorative image cannot be avoided then either use blank ALT text or better still, let the user know it&#8217;s a decorative image and place it at the very bottom of your HTML source output.

## 7. Use CSS for presentation

It&#8217;s hard not to talk about CSS when talking about HTML. CSS complements HTML so well. I will only go briefly into CSS here but I&#8217;d recommend research into this topic if you&#8217;re really interested in writing “better” HTML. A good book to grab hold of is [CSS Mastery](http://www.cssmastery.com/) by Andy Budd. Another good way to learn more about CSS is to view the CSS source of other people, see how they are doing things, learn from the experts! [Blueprint](http://code.google.com/p/blueprintcss/) and [YUI](http://developer.yahoo.com/yui/) have built CSS frameworks and is a good starting point for improving your own CSS skills. I don&#8217;t recommend using a framework per se but use it as a learning tool! Blueprint&#8217;s typography CSS is especially good. Investigate, learn and integrate.

Though CSS is used for presentation class names should not be based on presentational cues. Use [semantic-class-names](http://microformats.org/wiki/semantic-class-names) at all times. Example:

BAD: redtext, boldtext, smallIcon and leftnav.  
GOOD: note, important, attachments and subnav

## +7 Ways It Will Benefit Your Online Business

OK, so all this talk about writing &#8220;better&#8221; HTML seems like a waste of time. Why concentrate on this when you could work on more important aspects of your site? Such as a better design, cool Ajax features, and marketing! Well HTML **is** important and is one of the most important ones to get right! Here are 7 reasons why writing better HTML will benefit your business. _(It&#8217;s not just for the sake of ego and beauty or keeping your geeks busy!)_

  * ### Your pages will load faster
    
    Because you removed much of the clutter of TABLE and spacer GIFs your pages will load faster.</li> 
    
      * ### Lower your hosting costs
        
        Due to the reduced mark-up the total weight of your web page will be lower hence lowering payload, bandwidth and ultimately hosting and data transfer costs</li> 
        
          * ### Lower the cost of a redesign
            
            Your website no longer contains presentational mark-up hence it&#8217;s more receptive to change. A change of design mostly consists of graphic and CSS modifications. The underlying HTML structure doesn&#8217;t have to change much and in some cases it doesn&#8217;t have to change at all!</li> 
            
              * ### Maintain visual consistency
                
                Again, all presentational aspects have been moved to CSS so the write once use everywhere approach is used. In that CSS templates are created and applied across the board, hence it&#8217;s much easier to keep branding and design consistency.</li> 
                
                  * ### Get better search engine results
                    
                    Reduced clutter means your content can dominate the page and moved higher to the top of the HTML source output. Hence it is more favourable with search engines. Plus, by providing a document outline via headings you are giving a page more keyword relevance. Therefore, cleverly thought out headings that include relevant keywords will improve search engine rankings.</li> 
                    
                      * ### More accessible to all viewers
                        
                        As we&#8217;ve now removed all clutter and provided section headings, alt text, and link titles pages become more accessible instantaneously. Not only to humans but to search engines alike. Remember, Google is blind! Google does not understand JavaScript (yet), it relies on headings to determine relevance, it reads the alt text to understand image content and it follows links of interest.</li> 
                        
                          * ### It&#8217;s a winner!
                            
                            The Web Standards war has been won. So it&#8217;s here to stay whether you like it or not and will only grow in force as time goes by. If you don&#8217;t take note of it now your business will lose out in the long run and you _will_ be playing catch-up. So get on the Web Standards bandwagon now! And write _better_ HTML!</li> </ul> 
                            
                            Further reading:
                            
                              * <cite><a href="http://www.xml.com/pub/a/w3j/s1.people.html">The Web is Ruined and I Ruined It</a></cite> — <cite><a href="http://www.xml.com/pub/au/41">David Siegel</a></cite>
                              * <cite><a href="http://www.alistapart.com/articles/frameworksfordesigners/">Frameworks for Designers</a></cite> — <cite><a href="http://www.alistapart.com/authors/c/jeffcroft">Jeff Croft</a></cite>
                              * [HTML Mastery](http://htmlmastery.com/) by Paul Haine
                              * [CSS Mastery](http://www.cssmastery.com/) by Andy Budd
                              * [Transcending CSS](http://www.transcendingcss.com/) by Andy Clarke
                              * [Designing with standards, second edition](http://www.zeldman.com/dwws/) by Jeffery Zeldman