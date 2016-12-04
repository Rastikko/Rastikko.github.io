---
layout: post
title:  "Data Structures Cheat Sheet"
description: "A quick cheat sheet for dat structures, adding complexity and a implementation sample in java"
date:   2016-12-03
categories: html
---

## List ADT

The [list abstract data structure](https://goo.gl/mhgkxI) is one of the basic data structures around. Allows you to dynamically insert and remove and access elements.

<table class="table">
  <tr>
    <th class="span3">Signature</th>
    <th class="span2">Cost</th>
    <th class="span2">Java Implementation</th>
    <th class="span5">Description</th>
  </tr>
  <tr>
    <td><pre>boolean add(E e)</pre></td>
    <td>O(1)</td>
    <td><a href="https://docs.oracle.com/javase/7/docs/api/java/util/LinkedList.html#add(E)">add</a></td>
    <td>Appends the specified element to the end of this list (optional operation)</td>
  </tr>
  <tr>
    <td><pre>E get(int index)</pre></td>
    <td>O(n)</td>
    <td><a href="https://docs.oracle.com/javase/7/docs/api/java/util/LinkedList.html#get(int)">get</a></td>
    <td>Returns the element at the specified position in this list.</td>
  </tr>
  <tr>
    <td><pre>E set(int index, E element)</pre></td>
    <td>O(n)</td>
    <td><a href="https://docs.oracle.com/javase/7/docs/api/java/util/LinkedList.html#get(int)">TODO</a></td>
    <td>Replaces the element at the specified position in this list with the specified element (optional operation).</td>
  </tr>
  <tr>
    <td><pre>void add(int index, E element)</pre></td>
    <td>O(n)</td>
    <td><a href="https://docs.oracle.com/javase/7/docs/api/java/util/LinkedList.html#get(int)">TODO</a></td>
    <td>Inserts the specified element at the specified position in this list (optional operation). Shifts the element currently at that position (if any) and any subsequent elements to the right (adds one to their indices).</td>
  </tr>
  <tr>
    <td><pre>E remove(int index)</pre></td>
    <td>O(n)</td>
    <td><a href="https://docs.oracle.com/javase/7/docs/api/java/util/LinkedList.html#get(int)">TODO</a></td>
    <td> Removes the element at the specified position in this list (optional operation). Shifts any subsequent elements to the left (subtracts one from their indices). Returns the element that was removed from the list.</td>
  </tr>
</table>
