---
layout: post
title:  "Javascript Heap Data Structure"
description: "A heap implementation for javascript"
date:   2022-03-21
categories: algorithms
---

Here is an implementation of a data structure in javascript that allow us to define both min and max heap with the same code but using a comparator.

```js
const maxHeap = new Heap(MAX_HEAP_COMPARATOR, []);
const minHeap = new Heap(MIN_HEAP_COMPARATOR, []);
```
Also if you want to sort an array using the class here is an example:

```js
function heapSort(array) {
	const maxHeap = new Heap(MAX_HEAP_COMPARATOR, array);
	const sortedArray = maxHeap.getSortedArray();
	return sortedArray;
}
```

Of course this is only for educational purposes, you should probably use (Array.prototype.sort())[https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/sort] in production.

Implementation

```js
class Heap {
	constructor(comparator, array)
	{
		this.comparator = comparator;
		this.buildHeap(array);
	}
	
	getSortedArray()
	{
		for (let i = this.length - 1; i > 0; i--)
		{
			this.swap(0, i);
			this.length--;
			this.hepify(0);
		}
		return this.heap;
	}
	
	left(i)
	{
		return i * 2 + 1;
	}
	
	right(i)
	{
		return i * 2 + 2;
	}
	
	parent(i)
	{
		// returns -1 if no parent
		return Math.floor((i - 1) / 2);
	}
	
	buildHeap(array)
	{
		this.length = array.length;
		this.heap = array;
		const firstParentIndex = this.parent(array.length-1);
		for (let i = firstParentIndex; i >= 0; i--)
		{
			this.hepify(i);
		}
	}
	
	hepify(index)
	{
		let left = this.left(index);
		let right = this.right(index);
		let indexToSwap = index;

		if (left < this.length && this.comparator(this.heap[left], this.heap[indexToSwap]))
		{
			indexToSwap = left;
		}

		if (right < this.length && this.comparator(this.heap[right], this.heap[indexToSwap]))
		{
			indexToSwap = right;
		}
		
		if (indexToSwap !== index)
		{
			this.swap(index, indexToSwap);
			this.hepify(indexToSwap);
		}
	}
	
	peek()
	{
		return this.heap[0];
	}
	
	remove()
	{
		const removedValue = this.heap[0];
		this.heap[0] = this.heap.pop();
		this.length--;
		this.hepify(0);
		return removedValue;
	}
	
	insert(value)
	{
		this.length++;
		this.heap.push(value);
		
		let i = this.length - 1;
		while (i > 0 && this.comparator(this.heap[i], this.heap[this.parent(i)]))
		{
			this.swap(i, this.parent(i));
			i = this.parent(i);
		}
	}
	
	swap(i, j)
	{
		const temp = this.heap[i];
		this.heap[i] = this.heap[j];
		this.heap[j] = temp;
	}
}

const MAX_HEAP_COMPARATOR = (a,b) => a > b;
const MIN_HEAP_COMPARATOR = (a,b) => a < b;
```
