---
id: 95
title: 'JavaScript: Event Delegation'
date: 2008-08-21T21:18:54+00:00
author: caphun
layout: post
guid: http://yelotofu.com/?p=95
permalink: /2008/08/javascript-event-delegation/
dsq_thread_id:
  - "1241884584"
dsq_needs_sync:
  - "1"
categories:
  - Ramblings
tags:
  - eventdelegation
  - eventhandling
  - eventorder
  - Events
  - JavaScript
  - jQuery
---
Recently, I&#8217;ve been hearing much about event delegation. Many new to this concept seem to be baffled by the term. However, it really is a simple idea when you realise what&#8217;s involved.

Put simply, event delegation is the practice of directing events on parent DOM elements who then listen on their children for events.

To understand event delegation and why it works you should read this [ppk](http://www.quirksmode.org/about/intro.html) article before continuing &mdash; [JavaScript Event Order](http://www.quirksmode.org/js/events_order.html).

Back? OK, so now you know about event capturing and bubbling the concept is easier to comprehend.

Event delegation takes advantage of the fact that actions performed on a child element always bubbles up to the top. Traditionally events are handled on the element that fired it, for example (excuse my jQuery) :

<pre language="javascript">$('button').click(function(e) {
  alert('You clicked on me?');
});
</pre>

Now rather than handling the click event shown above on the element itself we could delegate it to a parent because we know all events eventually bubble to the top, so

<pre language="javascript">$('html').click(function(e) {
  if ( $(e.target).is('button') )
    alert('You clicked on me?');
});
</pre>

produces the same result as the first code snippet.

Did you notice `e.target`? This is the essence of event delegation. As the event bubbles it keeps a mental note of its starting position in its pocket; `e.target` is a reference to the first element the event started bubbling from. In the above code sample that would be `button`.

That&#8217;s event delegation in a nutshell!

Now, you might be asking &#8211; why should I use this rather than traditional one-to-one event handling?

Here are a few reasons:

  * In event delegation you bind one event handler to handle events on multiple elements. In traditional event handling you have to create a thousand event handlers to handle a thousand events. As you would expect event delegation is less resource expensive and could result in quicker response times
  * If Ajax or DOM manipulation happens, re-binding event handlers usually follow. Event delegation avoids re-binding by listening to a parent you know won&#8217;t be manipulated, i.e. `html`, `body` or the website container.
  * Event delegation makes for cleaner code if you have a large webapp demanding lots of event handling.
  * No need to worry about event order and bubbling issues as we&#8217;re now taking advantage of this effect

In conclusion. Event delegation is **not** a replacement for Event handling &#8211; both have their uses depending on situation. Event delegation requires more planning and could be harder to debug due to the inherent abstractions. You just can&#8217;t beat the humble event handler if all you want is a link opening in a new browser window. That said, you&#8217;d be mad not to use it if you have a complex app with thousands of event objects doing various operations from submitting a form to loading Ajax content.

Further reading:

  * [Event Delegation vs Event Handling](http://icant.co.uk/sandbox/eventdelegation/)
  * [Event Delegation Made Easy](http://www.danwebb.net/2008/2/8/event-delegation-made-easy-in-jquery)