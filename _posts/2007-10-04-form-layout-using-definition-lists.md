---
id: 47
title: Form Layout using Definition Lists
date: 2007-10-04T04:22:04+00:00
author: caphun
layout: post
guid: http://yelotofu.com/2007/10/form-layout-using-definition-lists/
permalink: /2007/10/form-layout-using-definition-lists/
dsq_thread_id:
  - "1246988055"
dsq_needs_sync:
  - "1"
categories:
  - Web Standards
tags:
  - CSS
  - definition list
  - dl
  - form
  - layout
  - tutorial
---
As you may well know, using a definition list (DL) to layout forms with labels and fields side-by-side could be a bit flaky at times; forms don&#8217;t seem to scale nicely and numerous layout problems could occur with dynamic content. Typical pitfalls are situations where a label or field takes up two or more lines or a BR tag in the DD column breaking things. After some playing around and testing I finally came to an elegant and bulletproof solution.

<pre lang="css">dl {clear:both;}
dt {float:left; clear:left;}
dd {overflow:hidden; clear:right; height:1%;}</pre>

The above CSS snippet will float the DT tag to the left. Then the DD tag will snug nicely to the right of it. The clever thing is if the content within the DD tag spans more than one line it will be indented by the width of the DT column. Try it!

However, our form looks a bit messy at the moment as the width of the DT column is determined by its content. Hence form fields and labels don&#8217;t align properly. To resolve this all we do is add a fixed width to the DT column.

<pre lang="css">dt {width:10em;}</pre>

Now, we&#8217;re faced with yet another problem. If the contents of the DT tag spans more than two lines it will occupy the space of the DT tag below it, pushing all the other DTs down causing misalignment of the DT &#8211; DD rows. To resolve this we add an additional empty DD tag for clearing, which we place below the actual DD containing content.

<pre lang="css">dd.x-form-clear {clear:both;}</pre>

To complete this post here&#8217;s an [example form layout using definition lists](http://yelotofu.com/demo/dl-form-layout.html "Form layout using a definition list").