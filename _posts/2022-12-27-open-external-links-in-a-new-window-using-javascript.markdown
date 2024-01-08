---
layout: post
title: "Open External Links in a New Window Using JavaScript"
description: "Open External Links in a New Window Using JavaScript"
categories: [Blog]
tags: [blog, external-links]
published: true
sitemap: true
pin: false
---


This is a quick post showing how to use JavaScript to make links to external websites open in a new window (or tab) instead of in the current window. This is useful for ```Jekyll``` blogs because the Markdown converters don’t do this for you. I included two versions: one that uses straight JavaScript, and one that requires ```jQuery``` but is shorter.

Both versions work basically the same way: grab all anchor tags ```<a href="#">``` that are linking to somewhere other than your development environment or a page on your site and then attribute ```target="_blank"``` to those tags. Because this is JavaScript, users with JavaScript disabled will still experience the old behavior, but otherwise won’t be adversely affected.


### Straight JavaScript
This version does not require any jQuery (or any other libraries):

```js
function ready(fn) {
  if (document.readyState != 'loading') {
    fn();
  } else if (document.addEventListener) {
    document.addEventListener('DOMContentLoaded', fn);
  } else {
    document.attachEvent('onreadystatechange', function() {
      if (document.readyState != 'loading')
        fn();
    });
  }
}

ready(function() {

  var website = window.location.hostname;

  var internalLinkRegex = new RegExp('^((((http:\\/\\/|https:\\/\\/)(www\\.)?)?'
                                     + website
                                     + ')|(localhost:\\d{4})|(\\/.*))(\\/.*)?$', '');

  var anchorEls = document.querySelectorAll('a');
  var anchorElsLength = anchorEls.length;

  for (var i = 0; i < anchorElsLength; i++) {
    var anchorEl = anchorEls[i];
    var href = anchorEl.getAttribute('href');

    if (!internalLinkRegex.test(href)) {
      anchorEl.setAttribute('target', '_blank');
    }
  }
});

```

### jQuery
This version requires jQuery in order to work, but if you’re using jQuery on your site anyway, it avoids reinventing the wheel:

```js
$(document).ready(function() {

  var website = window.location.hostname;

  var internalLinkRegex = new RegExp('^((((http:\\/\\/|https:\\/\\/)(www\\.)?)?'
                                     + website
                                     + ')|(localhost:\\d{4})|(\\/.*))(\\/.*)?$', '');

  $('a').filter(function() {
    var href = $(this).attr('href');
    return !internalLinkRegex.test(href);
  })
  .each(function() {
    $(this).attr('target', '_blank');
  });

});

```

### My Implementation for Jekyll Blog
I have created a file called [external-links-new-window.html](https://raw.githubusercontent.com/SamirPaulb/assets/main/external-links-new-window.html) inside ```_includes``` directory and referred it from ```_layouts/default.html``` as <a href="#"><img src="/assets/img/include-external-links-new-window.html-code.png" alt="external-links-new-window"  width="370px" height="22px"></a>.


