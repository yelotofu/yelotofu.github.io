---
id: 40
title: Building an Unobtrusive, Accessible and Standards Compliant Numeric Stepper
date: 2007-07-01T01:05:15+00:00
author: caphun
layout: post
guid: http://yelotofu.com/2007/07/building-an-unobtrusive-accessible-and-standards-compliant-numeric-stepper/
permalink: /2007/07/building-an-unobtrusive-accessible-and-standards-compliant-numeric-stepper/
dsq_thread_id:
  - "1241916068"
dsq_needs_sync:
  - "1"
categories:
  - Accessibility
  - JavaScript
tags:
  - Accessibility
  - CSS
  - formcontrol
  - JavaScript
  - numericstepper
  - unobtrusive
  - xhtml
---
First off, if you&#8217;re looking for a quick solution feel free to skip directly to the download link at the end of this article. For those who are interested in the intricate details please read on&#8230;

### What is a Numeric Stepper?

Well, the answer is simple. It&#8217;s a form control and looks like this&#8230;

<img src="http://yelotofu.com/demo/numeric_stepper/example_numeric_stepper.png" title="A Numeric Stepper" alt="A Numeric Stepper" height="22" hspace="10" vspace="10" width="46" /> 

It has an intuitive look that does not require much brain power to figure out how to use. The name itself suggests it&#8217;s restricted to numeric values. The plus and minus signs indicate an ability to step up or down. The steps must be of equal size maintaining consistency. The great thing about Numeric Steppers is users can either enter a value or use the plus and minus buttons to arrive at a target value.

Flash UI developers have long since enjoyed this form control. In fact, it wasn&#8217;t until Flash came out with their UI components before I even heard of a Numeric Stepper!

### What is it used for?

Numeric Steppers are not always useful. They are designed to solve a specific UI problem. Scenarios where Numeric Steppers would be of use are:

  * In shopping baskets; so users can quickly change quantities.
  * When choosing number of years experience in a skill or profession. Some forms may contain many such questions so Numeric Steppers will facilitate quick mouse action.
  * When choosing number of children or family members. There is no logical upper limit to this question so a drop down is out of the question. A simple input box will serve well but means the user will have to leave their mouse; find the correct keyboard key; then enter a value. With a Numeric Stepper they&#8217;d simply click the mouse button a few times in succession to obtain their target value.

These are just but a handful of scenarios. I&#8217;m sure there are much more good usage examples out there.

### Pity they didn&#8217;t think of it earlier?

There is no equivalent HTML form control for the Numeric Stepper. I guess when forms were conceived there was no urgent need for them or the concept just didn&#8217;t exist back then. The rise of Ajax and rich UI interfaces have boosted the industry&#8217;s appetite for greater interactivity in forms. The chances of a Numeric Stepper playing more useful roles in forms is much greater now.

With that thought in mind we start our journey on building our own&#8230;

### Building the Numeric Stepper

With help from JavaScript and a few basic form controls we can easily create our very own Numeric Stepper. The ingredients are: a standard text input, two buttons, a container to wrap it all up; and JavaScript to handle the associated events.

#### The HTML

<pre language="html">&lt;span class="numeric-stepper"&gt;
&lt;input name="ns_textbox" size="2" type="text" /&gt;
  &lt;button type="submit" name="ns_button_1" value="1" class="plus"&gt;+&lt;/button&gt;
  &lt;button type="submit" name="ns_button_2" value="-1" class="minus"&gt;-&lt;/button&gt;
&lt;/span&gt;
</pre>

[Example 1: The HTML structure](/demo/numeric_stepper/example_1.html)

You may notice submit buttons are used rather than &#8220;button&#8221; buttons. This is so if JavaScript is not available the Numeric Stepper will degrade gracefully. Clicking on the buttons will cause a form submit hence allowing developers to take event handling to the backend. I won&#8217;t go into details of how to do the backend as it&#8217;s out of the scope of this article.

I must stress that form submit on button click is NOT what we are after for JavaScript enabled browsers. Using unobtrusive Javascript we want to increment/decrement the input box value by a step size on button click. We also want the JavaScript to restrict it to numerical values only; and apply an upper and lower limit. The code is too much to present here so I&#8217;m only going to show the important parts:

#### The JavaScript

<pre language="javascript">var NumericStepper = {
  register : function(name, minValue, maxValue, stepSize){
    ...
    textbox.onkeypress = function(e){
      if(window.event){
        keynum = e.keyCode;
      } else if(e.which){
        keynum = e.which;
      }
      keychar = String.fromCharCode(keynum);
      numcheck = /[0-9-]/;
      if (keynum==8)
        return true;
      else
        return numcheck.test(keychar);
    };
    ...
  }
  ...
  ,stepper:function(textbox, val){
    if (textbox == undefined)
      return false;
    if (val == undefined || isNaN(val))
      val = 1;
      if (textbox.value == undefined || textbox.value == '' || isNaN(textbox.value))
        textbox.value = 0;
      textbox.value = parseInt(textbox.value) + parseInt(val);
      if (parseInt(textbox.value) &lt; NumericStepper.minValue)
        textbox.value = NumericStepper.minValue;
      if (parseInt(textbox.value) &gt; NumericStepper. maxValue)
        textbox.value = NumericStepper.maxValue;
    }
  ...
}
</pre>

[Example 2: Numeric Stepper; no clothes](/demo/numeric_stepper/example_2.html)

Our Numeric Stepper is nearly complete. It doesn&#8217;t look much like one at the moment; but with a little help from CSS we can give our Numeric Stepper some clothes.

#### The CSS

<pre language="css">.numeric-stepper {
  width:3.425em;
  height:1.6em;
  display:block;
  position:relative;
  overflow:hidden;
  border:1px solid #555;
}

.numeric-stepper input {
  width:75%;
  height:100%;
  float:left;
  text-align:center;
  vertical-align:center;
  font-size:125%;
  border:none;
  background:none;
}

.numeric-stepper button {
  width:25%;
  height:50%;
  font-size:0.5em;
  padding:0;
  margin:0;
  z-index:100;
  text-align:center;
  position:absolute;
  right:0;
}
.numeric-stepper button.minus {
  bottom:0;
}
</pre>

[The final product: Unobtrusive, Accessible and Standards compliant.](/demo/numeric_stepper/index.html)

The idea of clothes/skins is fascinating for our Numeric Stepper as it allows us to change its look and feel with some CSS trickery. Take a look at this [graphical example](http://yelotofu.com/demo/numeric_stepper/another_skin/index.html).

### The Source Code

You can get hold of version 0.1 of the Numeric Stepper source code by following this [download link](http://yelotofu.com/demo/numeric_stepper/ns_v001.zip).

I have tested it on FF2, Opera 8.5, IE5.5, IE6, IE7 and Safari. Works well but the buttons look a little weird in Safari though still usable.

Bugfixes, code enhancements, feature requests & improvements are welcome. Please do let me know if you use this code though and if you find it at all useful!

**Update:** [version 0.1.2](http://yelotofu.com/2008/01/unobtrusive-accessible-standards-compliant-numeric-stepper-revisited/) adds some accessibility enhancements.