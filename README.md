jquery.dragbettter
==================

An alternative to `dragenter` and `dragleave` events that fires each event once.


What this is all about
----------------------

There are two similar pairs of events that track mouse movement: `mousein`+`mouseout` and `mouseenter`+`mouseleave`. Let's say we're listening for these events on the `<body>` element. The `mouseenter` and `mouseleave` events would fire only when mouse pointer enters or leaves the `<body>` element itself. The `mousein` and `mouseout` events would trigger whenever mouse pointer crosses the border of any child within `<body>`, with `event.target` set to the child and the child's parent respectively.

The problem with the `dragenter` and `dragleave` events is that they work similar to `mousein` and `mouseout`. By March 2014, browsers do not provide drag-related events that would behave similar to `mouseenter`+`mouseleave`.

This makes it hard to track dragged file entering/leaving a region, especially when the region is the whole page.

**jquery.dragbettter** is a jQuery plugin that introduces two events: `dragbetterenter` and `dragbetterleave` that behave similar to `mouseenter`+`mouseleave`, i. e. fire only for the element itself and not for its children.


How to use
----------

1. Include jQuery and jquery.dragbetter somewhere on your page:

  ```html
  <script type="text/javascript" src="http://code.jquery.com/jquery-latest.min.js"></script>
  <script type="text/javascript" src="/js/jquery.dragbetter.js"></script>
  ```

2. Listen to `dragbetterenter` and `dragbetterleave` events on an element:

  ```js
  var $dropzones = $('.dropzone');

  $('body')
    .on('dragbetterenter', function() {
      $dropzones.addClass('highlighted');
    })
    .on('dragbetterleave', function() {
      $dropzones.removeClass('highlighted');
    })
  ```

  Don't forget to either include this code after your HTML or wrap it with `$(document).ready( function () { /*...*/ });`.
  

Demo
----

Here's a simple demonstration: http://jsbin.com/xexub/1/edit?html,css,js,output


Things to keep in mind
----------------------

- The `dragbetterenter` and `dragbetterleave` events work in pair. They won't work without each other, so attach to both of them on the same element. Attach to `dragbetterenter` first.
- The callback function accepts an `event` argument as usual. `event.target` will always be equal to the HTML element the event was attached to.
- The `dragbetterleave` event will also trigger when there has been a drop inside the element, so that you can remove highlighting after the drop. You should use the normal `drop` event to perform drop-related actions.


Credits
-------

Author: Andrey 'lolmaus' Mikhaylov
E-mail: lolmaus@gmail.com

Sponsored by [Hivemind](http://hiveminded.net/).

Based on [jquery.draghover.js](https://gist.github.com/meleyal/3794126) by William Meleyal (william.meleyal@gmail.com).

Inspired by [jquery.event.dragout](https://github.com/dancork/jquery.event.dragout) by Dan Cork ([Firstname].[Lastname]@kickinteractive.net).

Thanks to Ian Bytchek for support.
