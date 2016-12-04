---
layout: post
title:  "Data Structures Cheat Sheet"
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


### Queue ADT

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
    <td>O(n)</td>
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
  <tr>
    <td><pre>int size()</pre></td>
    <td>O(1)</td>
    <td><a href="https://docs.oracle.com/javase/7/docs/api/java/util/Collection.html#size()">remove</a></td>
  </tr>
</table>

### LIFO Queue (Stack)

### Priority Queue
