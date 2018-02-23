---
layout: post
title:  "3 Tips and Tricks with Promises"
description: "How to use stylus to loop through an array of values and assign theese to an element"
date:   2017-03-02
categories: js
---

These are some small tricks I found usefull working as a web developer, they all involve the usage of [Promises](https://developer.mozilla.org/es/docs/Web/JavaScript/Referencia/Objetos_globales/Promise).

## 1 Wrap a XHR request in a promise

Sometimes can be handy to just leverage a promise instead of the callbacks that a json request might trigger. Here is a snnipet to dot that:

```js
function getJSONPromise(url) {
  return new Promise(function(resolve, reject) {

    const xhr = new XMLHttpRequest();

    xhr.overrideMimeType("application/json");
    xhr.open('GET', url, true);
    xhr.timeout = 2000;

    xhr.onload = function() {
      try {
        resolve(JSON.parse(xhr.responseText));
      } catch (e) {
        error('Caught in _loadJSON() ', e);
        reject();
      }
    };

    // to handle networking errors
    xhr.onerror = reject;
    xhr.ontimeout = reject;
    xhr.onabort = reject

    xhr.send();
  });
}
```

## 2 Race against a timeout

Sometimes you expect that a promise will never resolve, this will help to deal with that.

```js
const timeoutPromise = new Promise((resolve, reject) => window.setTimeout(reject, 10000));
const anotherPromise = //...

Promise.race([timeoutPromise, anotherPromise]).then( //...
```

## 3 Ensure an element is rendered through requestAnimationFrame

[Swizec Teller](https://swizec.com/blog/how-to-properly-wait-for-dom-elements-to-show-up-in-modern-browsers/swizec/6663) shows in his blog how we can use `requestAnimationFrame`, we can leverage this pattern through a Promise:

```js
function getElementRenderedPromise(domElement) {
  return new Promise(resolve => {
    const check = function() {
      if (!domElement.offsetWidth) {
        window.requestAnimationFrame(check);
      } else {
        resolve();
      }
    }
    check();
  });
}
```
