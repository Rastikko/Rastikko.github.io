---
layout: post
title:  "How Flexible Box layout Module works"
description: "Introduction of browser DOM elements flow and how the positioning works through CSS specifications"
date:   2016-05-04
categories: html
---

The flexbox is a [CSS3 module specification](https://www.w3.org/TR/css-flexbox-1/), meaning that it belong to the new specs for the web. This specification allow us to laying down complex applications and websites. But for us fully understand what this new spec is capable to do, we should step back, and try to trace the CSS 2.1 specifications about normal flow, also we should mention how positioning works.

### Normal flow

This explains how the positioning of elements will adjust against others. Base on [CSS 2.1](https://www.w3.org/TR/CSS21/visuren.html#normal-flow) specification:

> Boxes in the normal flow belong to a formatting context, which may be block or inline, but not both simultaneously. Block boxes participate in a block formatting context. Inline boxes participate in an inline formatting context.

You might set up the formatting context through the [display](https://developer.mozilla.org/en-US/docs/Web/CSS/display) CSS property. For example the values `block`, `list-item` and `table` would set up the block formatting (elements would be shown one over another), where the values `inline`, `inline-table` and `inline-block` would set up the inline formatting (elements would be shown one next to another).

### Positioning

In normal flow the default position of an element is `static`, meaning that is not positioned. You might use the position attribute to set up the position of an element:

```css
.my-selector {
  position: relative;
  position: absolute;
  position: fixed;
}
```

Once you define a position you might use the properties `top`, `left`, `right` and `left` to define where to put your element. Note that this position will be relative on the closer *offsetParent*

> The offsetParent it's the closer parent element that have a position defined (static does not count), if none of this parents have a position, then the body will become the offsetParent.

For example a good strategy to position absolute but from a relative parent, it's the use of position `relative` into `absolute` of a parent/child relationship:

```css
.parent-container {
  position: relative;
}

.child-element {
  position: absolute;
  top: 20px;
  left: 20px;
}
```

Meaning that the offsetParent of `child-element` is `parent-container`. Last thing to note, even if relative position behaves like a static, it will allow you to define position attributes into the element.

### Flexible box
Alternative, in CSS3 there is a new [flexbox module](https://www.w3.org/TR/css-flexbox-1/#flex-containers), flex layout allow us to to have a more controlled flow of the elements, allowing us to organize the flow of multiple elements in a more controlled way. [Check this guide](https://css-tricks.com/snippets/css/a-guide-to-flexbox/) to know more about flexbox.

TODO: add one example of each
 - can be laid out in any flow direction (leftwards, rightwards, downwards, or even upwards!)
 - can have their display order reversed or rearranged at the style layer (i.e., visual order can be independent of source and speech order)
 - can be laid out linearly along a single (main) axis or wrapped into multiple lines along a secondary (cross) axis
 - can “flex” their sizes to respond to the available space
 - can be aligned with respect to their container or each other on the secondary (cross)
 - can be dynamically collapsed or uncollapsed along the main axis while preserving the container’s cross size

 - https://www.w3.org/TR/css-flexbox-1/
