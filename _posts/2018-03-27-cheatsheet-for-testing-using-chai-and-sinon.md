---
layout: post
title:  "Cheatsheet to test using Mocha, Chai and Sinon"
description: "Quick cheatsheet with the different assertions and spies and stub snnippets for succesfully testing in javascript."
date:   2018-03-27
categories: javascript
---

This is a little cheatsheet with snnipets to create unit tests using Mocha test runner, Chai assertion library and Sinon (for spies and stubs).

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

## Mocha only and skip
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

```js
it('mocha can done callback', function(done) {
    testSubject.getPromiseMethod().then(function(data) {
        expect(data).to.equal('Resolved!');
        done();
    });
});
```
## Mocha return a promise

```js
it('mocha can handle returned promises', function() {
    return testSubject.getPromiseMethod().then(function(data) {
        expect(data).to.equal('Resolved!');
    });
});
```

## Chai contains and handleling arrays
```js
    it('can check if it contains a method', function() {
        expect(testSubject.getArray()).include(2);
    });
```
## Chai contains and handleling objects

```js
it('can check if it contains element in object', function() {
    expect(testSubject.getObject()).include({one: 'a'});
});
```

## Sinon spy a call count

```js
cont numberOfCalls = spy.callCount;
```

## Sinon spy a call arguments

```js
const firstCallFirstArgumentValue = spy.args[0][0];
```

## Sinon spy called with arguments

```js
const booleanCalled = spy.withArgs('MY_FIRST_ARGUMENT').calledOnce;
```

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

## Sinon stub an object

```js
sinon.stub(objectToStub, 'propertyWeAreStubbing').value({
  propertyMethod: sinon.stub()
});
```

## Sinon stub a method with different output per argument

## Sinon use sandbox feature


