---
id: 951
title: inlineEdit and AngularJS
date: 2013-04-27T17:08:12+00:00
author: caphun
layout: post
guid: http://www.yelotofu.com/?p=951
permalink: /2013/04/inlineedit-and-angularjs/
dsq_thread_id:
  - "1241677160"
dsq_needs_sync:
  - "1"
categories:
  - AngularJS
  - jQuery
tags:
  - angularjs
  - directive
  - inlineedit
  - jQuery
---
Recently I used the [inlineEdit plugin](https://github.com/caphun/jquery.inlineedit) with a project that uses AngularJS. As the inlineEdit plugin only handles switching between non-editable and editable views and exposes the save/cancel actions it was pretty easy to integrate. What I ended up doing was wrap the inlineEdit plugin with a Directive that implements the [ngModelController](http://docs.angularjs.org/api/ng.directive:ngModel.NgModelController) API.



<a href="http://htmlpreview.github.com/?https://github.com/caphun/jquery.inlineedit/blob/master/demos/angular.html " target="_blank">Take a look at the demo</a>