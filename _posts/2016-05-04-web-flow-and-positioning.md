---
layout: post
title:  "Web flow and posititioning"
date:   2016-05-04
categories: html
---

In this article we will introduce some of the mayor concepts of browser DOM elements Positioning and how
the browser will render your html elements base on different style manipulations.

## Normal flow

Any element in the DOM structure will respect the normal flow by default. This flow could have 2 flaviours,
`block` or `inline`. You might set up the position of your element through the [display](https://developer.mozilla.org/en-US/docs/Web/CSS/display) property:

```css
.my-selector {
  display: block;
}
```

You might find more information in [W3C CSS Specification](https://www.w3.org/TR/CSS22/visuren.html#normal-flow).

## Positioning

Static, Relative, Absolute and Fixed.

## Calculating element position

Relative to the viewport/document
