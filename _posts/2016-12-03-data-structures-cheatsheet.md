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
    <th>Data Structure</th>
    <th>Operation</th>
    <th>Cost</th>
    <th>Java Implementation</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>Linked List</td>
    <td></td>
    <td></td>
    <td>LinkedList</td>
  </tr>
  <tr>
    <td></td>
    <td>`boolean add(E e)`</td>
    <td>O(1)</td>
    <td><a href="https://docs.oracle.com/javase/7/docs/api/java/util/LinkedList.html#add(E)">add</a></td>
    <td>Appends the specified element to the end of this list (optional operation)</td>
  </tr>
  <tr>
    <td></td>
    <td>`E get(int index)`</td>
    <td>O(n)</td>
    <td><a href="https://docs.oracle.com/javase/7/docs/api/java/util/LinkedList.html#get(int)">get</a></td>
    <td>Returns the element at the specified position in this list.</td>
  </tr>
  <tr>
    <td></td>
    <td>`E set(int index, E element)`</td>
    <td>O(n)</td>
    <td>Replaces the element at the specified position in this list with the specified element (optional operation).</td>
  </tr>
  <tr>
    <td></td>
    <td>`void add(int index, E element)`</td>
    <td>O(n)</td>
    <td>Inserts the specified element at the specified position in this list (optional operation). Shifts the element currently at that position (if any) and any subsequent elements to the right (adds one to their indices).</td>
  </tr>
  <tr>
    <td></td>
    <td>`E remove(int index)`</td>
    <td>O(n)</td>
    <td> Removes the element at the specified position in this list (optional operation). Shifts any subsequent elements to the left (subtracts one from their indices). Returns the element that was removed from the list.</td>
  </tr>
</table>
