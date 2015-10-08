# scroll-to-next-anchor-at-mouse-wheel
Scroll to next anchor at mouse wheel

Explaination : 

The delay variable prevents the mouse wheel from scrolling too quickly. The entire function is wrapped in a closure, so delay remains a private variable.

To scroll to next anchor tag in the webpage, we use $(document).on('mousewheel') for most of the browsers, the only exception is firefox which works with $(document).on('DOMMouseScroll'), so we will take that into consideration.

We can get the direction of the mousewheel with event.originalEvent.wheelDelta for browers except firefox. For firefox we will need to use -event.originalEvent.detail.

Depending on the value of the above being -ve or +ve (-ve for scroll down and +ve for scroll up) we will come to know whether scrolled down or up.

If +ve (scroll up), loop through each tag beginning with the last, until its first getClientRects() top is < -20.

If -ve (scroll down),  loop through each tag beginning with the first, until its first getClientRects() top is >= 30. 

