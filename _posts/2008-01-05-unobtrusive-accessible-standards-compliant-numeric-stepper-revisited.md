---
id: 69
title: Unobtrusive, Accessible and Standards Compliant Numeric Stepper (revisited)
date: 2008-01-05T05:22:49+00:00
author: caphun
layout: post
guid: http://yelotofu.com/2008/01/unobtrusive-accessible-standards-compliant-numeric-stepper-revisited/
permalink: /2008/01/unobtrusive-accessible-standards-compliant-numeric-stepper-revisited/
dsq_thread_id:
  - "1244426359"
dsq_needs_sync:
  - "1"
categories:
  - Accessibility
  - JavaScript
tags:
  - Accessibility
  - accessible
  - dojo
  - dojotoolkit
  - html
  - JavaScript
  - numericspinner
  - numericstepper
  - unobtrusive
  - webstandards
---
July last year I wrote a small tutorial on how to build an [Unobrustive, Accessible and Standards Compliant Numeric Stepper](http://yelotofu.com/2007/07/building-an-unobtrusive-accessible-and-standards-compliant-numeric-stepper/). As of today it remains the most high traffic page on my site. I can see there _is_ interest out there in a HTML and JavaScript based Numeric Stepper since the most searched for terms are:

  1. javascript numeric stepper
  2. html numeric stepper
  3. numericstepper javascript

So with some downtime on my hands I did some code refactoring and added a few Accessibility improvements: Now, when the Textbox has focus pressing the up or down arrow cursor keys will increment or decrement the numeric value respectively. Also with the cursor keys you can now navigate between the Textbox and plus and minus buttons without resorting to the Mouse pointer.

[Test the new cursor key feature with this example](http://yelotofu.com/labs/numeric-stepper/version/0.1.2/ns-example.html)

As an aside, [the Dojo Toolkit](http://dojotoolkit.org) has a Numeric Stepper as part of [Dijit, the Dojo Widgit Library](http://dojotoolkit.org/book/dojo-book-0-9/part-2-dijit-0). They call it a [NumericSpinner](http://dojotoolkit.org/book/dojo-book-0-9/part-2-dijit/form-validation-specialized-input/number-spinner). It&#8217;s pretty powerful though looks bad with CSS switched off. Additionally, the Dojo Toolkit tends to add proprietary attributes to your HTML, hence breaking validation.

[Get latest version (NumericStepper v0.1.2)](http://yelotofu.com/labs/numeric-stepper/version/0.1.2/ns-0.1.2.zip)