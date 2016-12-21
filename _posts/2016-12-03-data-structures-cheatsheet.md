---
layout: post
title:  "Basic Data Structures Keynotes"
description: "A quick cheat sheet for dat structures, adding complexity and a implementation sample in java"
date:   2016-12-03
categories: html
---

## List ADT

The [list abstract data structure](https://goo.gl/mhgkxI) is one of the basic data structures around. Allows you to dynamically insert and remove and access elements.

### Linked List

<table class="table">
  <tr>
    <th class="span6">Signature</th>
    <th class="span3">Cost</th>
    <th class="span3">Implelementation</th>
  </tr>
  <tr>
    <td><pre>boolean add(E e)</pre></td>
    <td>O(1)</td>
    <td><a href="https://docs.oracle.com/javase/7/docs/api/java/util/LinkedList.html#add(E)">add</a></td>
  </tr>
  <tr>
    <td><pre>E get(int index)</pre></td>
    <td>O(n)</td>
    <td><a href="https://docs.oracle.com/javase/7/docs/api/java/util/LinkedList.html#get(int)">get</a></td>
  </tr>
  <tr>
    <td><pre>E set(int index, E element)</pre></td>
    <td>O(n)</td>
    <td><a href="https://docs.oracle.com/javase/7/docs/api/java/util/LinkedList.html#add(int,%20E)">add</a></td>
  </tr>
  <tr>
    <td><pre>E remove(int index)</pre></td>
    <td>O(n)</td>
    <td><a href="https://docs.oracle.com/javase/7/docs/api/java/util/LinkedList.html#remove(int)">remove</a></td>
  </tr>
</table>

### Array List

The size, isEmpty, get, set, iterator, and listIterator operations run in constant time. The *add operation runs in amortized constant time*, that is, adding n elements requires O(n) time. All of the other operations run in linear time (roughly speaking). The constant factor is low compared to that for the LinkedList implementation.

<table class="table">
  <tr>
    <th class="span6">Signature</th>
    <th class="span3">Cost</th>
    <th class="span3">Implelementation</th>
  </tr>
  <tr>
    <td><pre>boolean add(E e)</pre></td>
    <td>O(n)</td>
    <td><a href="https://docs.oracle.com/javase/7/docs/api/java/util/LinkedList.html#add(E)">add</a></td>
  </tr>
  <tr>
    <td><pre>E get(int index)</pre></td>
    <td>O(1)</td>
    <td><a href="https://docs.oracle.com/javase/7/docs/api/java/util/LinkedList.html#get(int)">get</a></td>
  </tr>
  <tr>
    <td><pre>E set(int index, E element)</pre></td>
    <td>O(1)</td>
    <td><a href="https://docs.oracle.com/javase/7/docs/api/java/util/LinkedList.html#add(int,%20E)">add</a></td>
  </tr>
  <tr>
    <td><pre>E remove(int index)</pre></td>
    <td>O(n)</td>
    <td><a href="https://docs.oracle.com/javase/7/docs/api/java/util/LinkedList.html#remove(int)">remove</a></td>
  </tr>
</table>


## Queue ADT

### FIFO Queue

You can implement it efficiently with a Linked List or Array List.

<table class="table">
  <tr>
    <th class="span6">Signature</th>
    <th class="span3">Cost</th>
    <th class="span3">Implelementation</th>
  </tr>
  <tr>
    <td><pre>boolean enqueue(E e)</pre></td>
    <td>O(1)</td>
    <td><a href="https://docs.oracle.com/javase/7/docs/api/java/util/Queue.html#add(E)">add</a></td>
  </tr>
  <tr>
    <td><pre>E dequeue()</pre></td>
    <td>O(1)</td>
    <td><a href="https://docs.oracle.com/javase/7/docs/api/java/util/Queue.html#remove()">remove</a></td>
  </tr>
  <tr>
    <td><pre>E peek()</pre></td>
    <td>O(1)</td>
    <td><a href="https://docs.oracle.com/javase/7/docs/api/java/util/Queue.html#peek()">peek</a></td>
  </tr>
</table>

### LIFO Queue (Stack)

Can be implemented efficiently using an Array List or Linked List.

<table class="table">
  <tr>
    <th class="span6">Signature</th>
    <th class="span3">Cost</th>
    <th class="span3">Implelementation</th>
  </tr>
  <tr>
    <td><pre>boolean push(E e)</pre></td>
    <td>O(1)</td>
    <td><a href="https://docs.oracle.com/javase/7/docs/api/java/util/Stack.html#push(E)">push</a></td>
  </tr>
  <tr>
    <td><pre>E dequeue()</pre></td>
    <td>O(1)</td>
    <td><a href="https://docs.oracle.com/javase/7/docs/api/java/util/Stack.html#pop()">pop</a></td>
  </tr>
  <tr>
    <td><pre>E peek()</pre></td>
    <td>O(1)</td>
    <td><a href="https://docs.oracle.com/javase/7/docs/api/java/util/Stack.html#peek()">peek</a></td>
  </tr>
</table>

### Dequeue

Is a double ended queue, elements can be added to the front or the back. Can be implemented efficiently in both doubly linked list and Array List (with the circular array list implementation).

### Binary Heaps

They help to implement [priority queues](https://docs.oracle.com/javase/7/docs/api/java/util/PriorityQueue.html) efficiently. The binary heap is a binary tree that needs to be completed. They contain a heap property, **Min Heap** where are the childrens have a priority less or equal than the parent or **Max heap** (viceversa).

<table class="table">
  <tr>
    <th class="span6">Signature</th>
    <th class="span3">Cost</th>
    <th class="span3">Implelementation</th>
  </tr>
  <tr>
    <td><pre>boolean add(E e)</pre></td>
    <td>O(lg(n))</td>
    <td><a href="https://docs.oracle.com/javase/7/docs/api/java/util/PriorityQueue.html#add(E)">add</a></td>
  </tr>
  <tr>
    <td><pre>E remove()</pre></td>
    <td>O(lg(n))</td>
    <td><a href="https://docs.oracle.com/javase/7/docs/api/java/util/PriorityQueue.html#poll()">poll</a></td>
  </tr>
</table>

## Set and Map ADT

They both can reuse the same implementation (a map is a set with an extra value field). The main caracteristic is that the elements never duplicates.

### Binary Search Tree

Is important to note that this operations cost are only for self balance trees, like example [AVL](https://en.wikipedia.org/wiki/AVL_tree) or [Red-black](https://en.wikipedia.org/wiki/Red%E2%80%93black_tree) trees. If they are regular trees, the operations can cost up to O(n).

BST allows you to manage the data in a sorted fashion (They produce Sorted Sets and Maps).

<table class="table">
  <tr>
    <th class="span6">Signature</th>
    <th class="span3">Cost</th>
    <th class="span3">Implelementation</th>
  </tr>
  <tr>
    <td><pre>boolean add(E e)</pre></td>
    <td>O(lg(n))</td>
    <td><a href="https://docs.oracle.com/javase/7/docs/api/java/util/TreeSet.html#add(E)">add</a></td>
  </tr>
  <tr>
    <td><pre>boolean contains(E e)</pre></td>
    <td>O(lg(n))</td>
    <td><a href="https://docs.oracle.com/javase/7/docs/api/java/util/TreeSet.html#contains(java.lang.Object)">contains</a></td>
  </tr>
  <tr>
    <td><pre>boolean remove(E e)</pre></td>
    <td>O(lg(n))</td>
    <td><a href="https://docs.oracle.com/javase/7/docs/api/java/util/TreeSet.html#remove(java.lang.Object)">remove</a></td>
  </tr>
  <tr>
    <td><pre>traversal</pre></td>
    <td>O(n)</td>
    <td><a href="https://docs.oracle.com/javase/7/docs/api/java/util/TreeSet.html#iterator()">iterator</a></td>
  </tr>
</table>

### Hash Table

This class offers constant time performance for the basic operations (add, remove, contains and size), assuming the hash function disperses the elements properly among the buckets. Iterating over this set requires time proportional to the sum of the HashSet instance's size (the number of elements) plus the "capacity" of the backing HashMap instance (the number of buckets). Thus, it's very important not to set the initial capacity too high (or the load factor too low) if iteration performance is important.

<table class="table">
  <tr>
    <th class="span6">Signature</th>
    <th class="span3">Cost</th>
    <th class="span3">Implelementation</th>
  </tr>
  <tr>
    <td><pre>boolean add(E e)</pre></td>
    <td>O(1)</td>
    <td><a href="https://docs.oracle.com/javase/7/docs/api/java/util/HashSet.html#add(E)">add</a></td>
  </tr>
  <tr>
    <td><pre>boolean contains(E e)</pre></td>
    <td>O(1)</td>
    <td><a href="https://docs.oracle.com/javase/7/docs/api/java/util/HashSet.html#contains(java.lang.Object)">contains</a></td>
  </tr>
  <tr>
    <td><pre>boolean remove(E e)</pre></td>
    <td>O(1)</td>
    <td><a href="https://docs.oracle.com/javase/7/docs/api/java/util/HashSet.html#remove(java.lang.Object)">remove</a></td>
  </tr>
  <tr>
    <td><pre>traversal</pre></td>
    <td>O(n)*</td>
    <td><a href="https://docs.oracle.com/javase/7/docs/api/java/util/HashSet.html#iterator()">iterator</a></td>
  </tr>
</table>
