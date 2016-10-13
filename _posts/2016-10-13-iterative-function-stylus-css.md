---
layout: post
title:  "Iterate through a function in css stylus"
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

You can test it in [Try Stylus!](http://stylus-lang.com/try.html#?code=apply-field-sizes(%24element)%20%7B%0A%20%20%24field_sizes%20%3D%20(%2010%25%2020%25%2020%25%2020%25%2020%25%205%25%205%25%20)%3B%0A%20%20for%20value%2C%20key%20in%20%24field_sizes%20%7B%0A%20%20%20%20%0A%20%20%20%20%7B%24element%7D%3Anth-child(%7Bkey%20%2B%201%7D)%20%7B%0A%20%20%20%20%20%20width%3A%20value%3B%0A%20%20%20%20%7D%0A%20%20%7D%0A%7D%0A%0A.my-table-head%20%7B%0A%20%20th%20%7B%0A%20%20%20%20color%3A%20white%3B%0A%20%20%7D%0A%0A%20%20apply-field-sizes(th)%3B%0A%7D) and play with it.
