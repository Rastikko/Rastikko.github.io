---
layout: post
title:  "Iterate Through a function in css stylus"
description: "How to use stylus to loop through an array of values and assign theese to an element"
date:   2016-10-13
categories: css
---

Sometimes you need to be able to implement a quick function that will iterate through an array and assign values to it.
This quick snnipet can Help you to do this:

```stylus
apply-field-sizes($element) {
  $field_sizes = ( 10% 20% 20% 20% 20% 5% 5% );
  for value, key in $field_sizes {
    
    {$element}:nth-child({key}) {
      width: value;
    }
  }
}

.my-table-head {
  th {
    color: white;
  }

  apply-field-sizes(th);
}

```
