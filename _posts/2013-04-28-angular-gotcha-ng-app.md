---
id: 966
title: 'Angular gotcha: ng-app=&#8221;myApp&#8221; (named applications)'
date: 2013-04-28T17:52:41+00:00
author: caphun
layout: post
guid: http://www.yelotofu.com/?p=966
permalink: /2013/04/angular-gotcha-ng-app/
dsq_thread_id:
  - "1242006784"
dsq_needs_sync:
  - "1"
categories:
  - AngularJS
tags:
  - angularjs
  - facepalm
  - gotcha
---
<a href="http://angularjs.org/" target="_blank">Angular</a> is magical. The magic starts happening simply like so:

<pre language="html">&lt;html ng-app&gt;
  &lt;script src="angular.min.js"&gt;&lt;/script&gt;
  There are {{ 1 + 2 }} apples in the basket.
&lt;/html&gt;
</pre>

Which outputs:

<pre>There are 3 apples in the basket.</pre>

However, when the magic stops you could be left tearing your hair out finding the correct potion! 

For example, if you change `ng-app` to `ng-app="myApp"` you will see `{{ 1 + 2 }}` outputted instead of `3` with the following error:

<img src="http://yelotofu.s3.amazonaws.com/wp-content/uploads/2013/04/ng-app-gotcha.png" alt="ng-app-gotcha" width="682" height="291" class="alignnone size-full wp-image-1000" /> 

OK, that kinda makes sense as we&#8217;ve not created a module named <kbd>myApp</kbd>. 

Right, let&#8217;s do that:

<pre language="html">&lt;html ng-app=<span style="color:red;font-weight:bold">"myApp"</span>&gt;
  &lt;script src="angular.min.js"&gt;&lt;/script&gt;
  <span style="color:red;font-weight:bold">&lt;script&gt;
    var myApp = angular.module('myApp');
  &lt;/script&gt;</span>

  There are {{ 1 + 2 }} apples in the basket.
&lt;/html&gt;
</pre>

Hrm, well the magic still isn&#8217;t working! And we&#8217;re hit with a double whammy!

<img src="http://yelotofu.s3.amazonaws.com/wp-content/uploads/2013/04/ng-app-gotcha-2.png" alt="ng-app-gotcha-2" width="682" height="291" class="alignnone size-full wp-image-1002" /> 

<a href="http://docs.angularjs.org/api/angular.module" target="_blank">Digging a bit</a> into what&#8217;s happening with `angular.module`. Apparently, its method signature is:

<pre language="javascript">angular.module(name[, requires], configFn);
</pre>

Where `requires` is optional, however, <q>If specified then new module is being created. If unspecified then the the module is being retrieved for further configuration.</q> Aha! So the second parameter is required if creating a module!

<pre language="html">&lt;html ng-app="myApp"&gt;
  &lt;script src="angular.min.js"&gt;&lt;/script&gt;
  &lt;script&gt;
    var myApp = angular.module('myApp', <span style="color:red;font-weight:bold">[]</span>);
  &lt;/script&gt;

  There are {{ 1 + 2 }} apples in the basket.
&lt;/html&gt;
</pre>

Facepalm!

**Note:** All tests done with the current stable release of Angular version 1.0.6.