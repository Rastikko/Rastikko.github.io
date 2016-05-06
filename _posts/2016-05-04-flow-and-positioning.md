---
layout: post
title:  "Flow and Positioning"
description: "Introduction of browser DOM elements flow and how the positioning works through CSS specifications"
date:   2016-05-04
categories: html
---

In this article we will introduce some of the mayor concepts of browser DOM elements Positioning and how
the browser will render your html elements base on different style manipulations.


### Normal flow

Any element in the DOM structure will respect the normal flow by default. This flow could traditionally had 2 flavors,
`block` or `inline`. You might set up the position of your element through the [display](https://developer.mozilla.org/en-US/docs/Web/CSS/display) property:

```css
.my-selector {
  display: block;
  display: inline;
  display: flex;
}
```

Alternative, in CSS3 there is a new [flexbox module](https://www.w3.org/TR/css-flexbox-1/#flex-containers), flex layout allow us to to have a more controlled flow of the elements, allowing us to organize the flow of multiple elements in a more controlled way. [Check this guide](https://css-tricks.com/snippets/css/a-guide-to-flexbox/) to know more about flexbox.

To read more about the normal flow, you might find information in the [W3C CSS Specification Normal Flow](https://www.w3.org/TR/CSS22/visuren.html#normal-flow).

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
