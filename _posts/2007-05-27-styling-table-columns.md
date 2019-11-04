---
id: 21
title: Styling table columns
date: 2007-05-27T01:47:09+00:00
author: caphun
layout: post
guid: http://yelotofu.com/2007/05/styling-table-columns/
permalink: /2007/05/styling-table-columns/
categories:
  - CSS
tags:
  - adjacent sibling
  - adjacentsibling
  - colgroup
  - ff2
  - ie7
  - selectors
---
The Colgroup element has existed for quite some time now. Its purpose is column grouping. It&#8217;s also in the class of under used elements. With Colgroup each column can be styled individually in a way similar to how we style table rows. Unfortunately most of todays browsers do not fully support the styling capabilities of Colgroup. FF2 only allows you to style the width and background-color properties whereas IE7 allows anything. Admittedly IE7 is the winner here. You can pretty much give a Colgroup element any style and IE7 will happily apply it to the table. Take a look at this [basic Colgroup example](http://yelotofu.com/demo/table_example/basic.html) and compare the difference between FF2 and IE7.

It&#8217;s quite dis-heartening news. However, there is a workaround. And it&#8217;s in the form of valid CSS. The adjacent sibling selector (+) could be used to select the n<sup>th</sup> cell of a table row. 99% of the time we&#8217;d be dealing with fixed column data. Therefore we could programatically retreive the correct column to style on a per row basis. Take the following example. To select the second column we&#8217;d do:

    td:first-child+td {
      put your column style here...
    }

Now to select the fifth column just carry on with the plus&#8217;:

    td:first-child+td+td+td+td {
      put your column style here...
    }

It&#8217;s not elegant, I know, but the beauty of this approach is that both FF2 and IE7 supports both + and first-child selectors. And as far as I&#8217;m aware the latest <acronym title="Mozilla, Opera & Safari">MOS</acronym> browsers do too.

Note: IE6 does not understand any of the things I&#8217;ve mentioned here so please do take this article with a pinch of salt until IE6 is completely phased out.