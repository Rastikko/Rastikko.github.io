---
layout: post
title:  "Dynamic grouped bar chart with D3.js"
description: "Create a grouped dynamic bar chart with D3 javascript library using checkbox to change the data"
date:   2016-05-04
categories: html
---

Today i would like to introduce a little project I've been cooking, is a proof of concept using [D3.js](https://d3js.org/), a data visualization library for javascript.

In this tutorial we will learn how to create dynamic grouped bar chart. We will be showing the number of people peer age grouped by some of the USA states. You can check the final result in **[Codepen](https://codepen.io/Rastikko/full/GqNbqM/)**.

This project was based in **[another example](http://bl.ocks.org/mbostock/3887051)**, with the main difference that we will be able to update the desired population gap.

All right, the first step is going to be create the different checkboxes to select the population gab, for that we will use the help of 2 arrays, ids and ageNames.

```javascript
var ids = ['preeschol', 'gradeschooler', 'teen', ...];
var ageNames = ['Under 5 Years', '5 to 13 Years', '14 to 17 years', ...];

// Let's populate the categoeries checkboxes
d3.select('.categories').selectAll('.checkbox')
  .data(ids)
  .enter()
  .append('div')
  .attr('class', 'checkbox')
  .append('label').html(function(id, index) {
    var checkbox = '<input id="' + id + '" type="checkbox" class="category">';
    return checkbox + ageNames[index];
  });
```

The first thing you can notice is `select` and `selectAll`, these a [D3Selectors](https://github.com/d3/d3/wiki/Selections) and they are based in CSS3 selectors.

After that we will bind the ids with the `data` method to all the checkbox selected. This means that D3 will associate each element inside the id's array and execute the subsequent commands for each one detected. Using some helpers functions, now we create a div with a checkbox and label inside.

The next step is to create some scales and define a range:

```javascript
// the scale for the state age value
var x = d3.scale.linear().range([0, width]);
// the scale for each state
var y0 = d3.scale.ordinal().rangeBands([0, height], .1);
// the scale for each state age
var y1 = d3.scale.ordinal();
```

We use [scale](https://github.com/d3/d3/wiki/Ordinal-Scales) method to create a variaty of scales, in this case one of the type `linear` and two of the type `ordinal`. The scales will help us to retrieve data within certain range, thanks to [rangeBands](https://github.com/d3/d3/wiki/Ordinal-Scales#ordinal_rangeBands) we will be able later to define the width of the subcategory axis.

Now we should be able to create the main svg, this will be the *container* of the graph:

```javascript
var svg = d3.select('.graph').append('svg')
  .attr('width', width + margin.left + margin.right)
  .attr('height', height + margin.top + margin.bottom)
  .append('g')
  .attr('transform', 'translate(' + margin.left + ',' + margin.top + ')');
```

Now need to listen to the checkboxes changes to render the graph, here is the snnipet:

```javascript
d3.select('.categories').selectAll('.category').on('change', function() {
  var x = d3.select('.categories').selectAll('.category:checked');
  var ids = x[0].map(function(category) {
    return category.id;
  });
  updateGraph(ids);
});
```

This is some more D3 overlapping jQuery, we will use the `.on(event)` method to trigger a function. This function will grab all the ids from the checkboxes and triger *updateGraph* to tell D3 to render the graph with the specifies ids. Now let's take a look of this update function:

```javascript
function updateGraph(selectedIds) {

  var statesData = ...
  /* we create the model of the data using selectedIds, should look like:
  [{
      state: 'CA',
      ages: [{
        id: 'adult',
        name: 'Between 5 and 10',
        value: 222111
      }, ...]
  }]
  */

```

Is improtant to note that the only factor that will change is the ages, the number of states will always be a constant. Now that we have defined the model of the updated data, is time to define the domains of the previously created scales:

```javascript
// x domain is between 0 and the maximun value in any ages.value
x.domain([0, d3.max(statesData, function(d) { return d3.max(d.ages, function(d) { return d.value }); })]);
// y0 domain is all the state names
y0.domain(statesData.map(function(d) { return d.state; }));
// y1 domain is all the age names, we limit the range to from 0 to a y0 band
// a band is something like height / nStates
y1.domain(ids).rangeRoundBands([0, y0.rangeBand()]);
```
Is time to focus in bars. First we need to create the groups that will represent each one of the different available

```javascript
var state = svg.selectAll('.state')
  .data(statesData);

state.enter()
  .append('g')
  .attr('class', 'state')
  .attr('transform', function(d) { return 'translate(0, ' + y0(d.state) + ')'; });
```
There are two new concepts here, first the `enter` function will tell D3 to only apply the following attributes when new data is *joined* to the selection. This means if data contain 2 elements but there are only 1 displayed in the DOM, anything after enter will be applied only to the second element. After we use the scale *y0* to define the position of the state.

All right, now for the abrs first we select all the rect (bars) inside each state. Then we define bind the data `age` from the parent object.


```javascript
var age = state.selectAll('rect')
  .data(function(d) { return d.ages; });
```

Now we need to define the states for `joined` (new elements) but also for `update`, to do that we execute the enter appending the new elements, but this time we don't concatenate directly the attributes. You can use this [example](http://bl.ocks.org/mbostock/3808218) to understand better the update pattern.

```javascript
// we append a new rect every time we have an extra data vs dom element
age.enter().append('rect');

// this updates will happend neither inserting new elements or updating them
age
  .attr('x', 0)
  .attr('y', function(d, index) { return y1(ids[index]); })
  .attr('id', function(d) { return d.id; })
  .style('fill', function(d) { return color(d.name); })
  .text(function(d) { return d.name })
  .transition()
  .attr('width', function(d) { return x(d.value); })
  .attr('height', y1.rangeBand());
```

Now note how we use the `transition` helper to define some animations over the width and height. Lastly, we need to define the exit state to make sure we remove any unused elements, with a fancy animation of curse :).

```javascript
// And we remove any elements no accounted with
age.exit().transition().attr('width', 0).remove();
```

There are some concepts like creating the axis or the legend that I did not covered in this article. I really invite you to check them out and play with them in the projects  [codepen](https://codepen.io/Rastikko/pen/GqNbqM).
