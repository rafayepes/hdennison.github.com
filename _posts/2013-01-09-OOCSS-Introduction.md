---
layout: post
tags: OOCSS
---
Basically, a **CSS “object”** is a repeating visual pattern, which can be
abstracted into an independent snippet of HTML, CSS, and possibly JavaScript.
Once created, an object can then be reused throughout a site.

A CSS object may be split in four layers:

* HTML, which can be one or more nodes of the DOM
* CSS declarations about the structure (base) of the object (display, size...)
* CSS declarations about the appearance of the object. (color, background...)
* JavaScript behaviors, listeners, or methods associated with the object.

Of course, we can have objects with no JS or CSS appearance styles, these are
base objects that can be extended in the future.

## Object example

### CSS
    /* Rank structure */
    .rank { width: 80px; background-position: 0 -16px; [...] }
    .rank, .rank::after { height: 16px; background-image: url("stars.png"); }
    .rank::after {
        position: absolute; top: 0; left: 0;
        background-position: 0 0;
        [...]
    }
    /* Rank modifiers */
    .rank-0::after { width: 0; }
    .rank-1::after { width: 16px; }
    .rank-2::after { width: 32px; }
    .rank-3::after { width: 48px; }
    [...]


### HTML Usage
    <!-- Any element with the CSS classes rank and rank-N -->
    <span class="rank rank-1"> 1 star </span>
    <div class="rank rank-2"> 2 stars </div>
    <whatever class="rank rank-3"> 3 stars </whatever>
    [...]


### Final result
<img alt="" src="data:image/png;base64,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" />