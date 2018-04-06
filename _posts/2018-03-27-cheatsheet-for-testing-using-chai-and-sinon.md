---
layout: post
title:  "Cheatsheet to test using Chai and Sinon"
description: "Quick cheatsheet with the different assertions and spies and stub snnippets for succesfully testing in javascript."
date:   2018-03-27
categories: javascript
---

## How to set them up with mocha
To start to setup your tests you need to define a test suite using `describe`. These act like closures and you can even nest them.

```js
describe('My feature test', function() {
    // ...
});
```

`describe.only` will ensure that only this test suite will run.

## Mocha before, beforeEach, after, afterEach
You can use before these to setup and restore any test helpers or components. You can even call these agains in nested describe.

```js
describe('My feature test', function() {
    let classToTest;
    beforeEach(function() {
        classToTest = new ClassToTest();
    });
    
    afterEach(function() {
        classToTest = null;
    });
});
```
## Mocha it
You use it to perform a test, it allows `it.only` will ensure that only this test will executed, `it.skip` will skip the test.

```js
it.only('should be able to get valueA', function() {
    //..
});

it.skip('this test is going to be skipped', function() {
    //..
});
```

## Mocha increase test timeout

## Mocha handle done callback

## Mocha return a promise

## Chai basic expect assertations

## Chai contains and handleling arrays

## Chai contains and handleling objects

## Sinon spy a call count

## Sinon spy a call arguments

```js
const spyCall = spy.withArgs('MY_FIRST_ARGUMENT');
```

## Sinon stub a function

## Sinon stub a method

```js
sinon.stub(objectToStub, 'propertyInObjectToStub').returns({
  propertyMethod: sinon.stub()
});
```

Then remember after the test is done to restore the origiinal object.

```js
objectToStub.propertyInObjectToStub.restore();
```

## Mocha handle promises
