---
id: 521
title: 'Tip: Obtaining Request Parameters in Zend_View'
date: 2009-08-06T23:11:43+00:00
author: caphun
layout: post
guid: http://yelotofu.com/?p=521
permalink: /2009/08/tip-request-params-in-zend_view/
categories:
  - PHP
---
I found it virtually impossible to obtain GET or POST request parameters in Zend\_View without resorting to accessing the $\_GET or $\_POST variables. Directly accessing these variables within Zend\_View is bad practice so it&#8217;s been suppressed on purpose to keep processing where it should be &#8211; within the Controller. However it is possible to get hold of these variables properly and that is to pass them from the Controller.

Example. You have a query string that looks like this `?keyword=test` and want to show it in your view, here&#8217;s what to do:

MyController.php

<pre language="php">public function indexAction() {
  $this-&gt;view-&gt;request = $this-&gt;getRequest();
}
</pre>

my-controller/index.phtml

<pre language="html">The keyword is &lt;?= $this-&gt;request-&gt;keyword ?&gt;
</pre>

Thanks!