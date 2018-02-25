---
layout: post
title:  "Create login acceptance test using Ember Mirage"
description: "We will discuss how to setup Ember CLI adding mirage and how to use it efficiently to backup your testing scenarios"
date:   2018-02-22
categories: ember.js
---

We will review how to install and use Ember Mirage, a Ember CLI Addon that allows you to mock server requests and response and provides a
fixture strategy.

## Installation

You can get more information in [Mirage installation page](http://www.ember-cli-mirage.com/docs/v0.4.x/installation/), but you can use:

```sh
ember install ember-cli-mirage
```

This will setup a **mirage** folder which contains the following subfolders:

 - **models**: they represent a mirage-base model (don't confuse with ember-data models), and they are use to understand what kind of attributes
 and relations they have between them.
 - **fixtures**: You can insert here raw endpoint data, is the faster way to start populating some data.
 - **factories**: A smart way to create endpoint data, allows you to define dynamic logic.
 - **scenarios**: Use this to change your development data without affecting your tests.
 - **serializers**: You can use to change the format of the server response.

## Setup the code

We are going to focus on creating some sort of dummy login feature, the objective is to be able to mock using Mirage 2 scenarios, the first one
is the scenario when the login is valid, in which case we should redirect to the index route. Otherwise we will show an authentication error.

We will use the help of a service and a component, they look pretty much like this:

```js
// app/services/session.js
export default Service.extend({
    user: null,

    isLoggedIn: computed.bool('user'),
    isLoginError: false,

    login: function(username) {
        return this.$.post('http://localhost:8080/api/v1/user/login', {username} ).then((data) => {
            if (!data.error) {
                this.set('user', data.user);
            }
        }).catch(() => {
            this.set('isLoginError', true);
        });
    },
});
```

Note that as today, mirage does not support `fetch` by default, [issue 983](https://github.com/samselikoff/ember-cli-mirage/issues/983), now lets
define our first integration test:

## Create the user model

We can do this with the following command:

```sh
ember g mirage-model user
```

## Create user factory

We need some user to test against, for that we can create a simple fixture like this one:

```js
// mirage/factories/users.js
import { Factory } from 'ember-cli-mirage';

export default Factory.extend({
    id: 1,
    name: 'Rastikko'
});


```

## Handle mirage Response

Now we need to create the Route Handler to handle both cases, the one that the user is not authorized (anything but the already created user),
or the success case:

```js
// mirage/config.js
this.post('/users/login', (schema, request) => {
    const name = JSON.parse(request.requestBody).name;
    if (name !== 'Rastikko') {
        return new Mirage.Response(401, {}, {message: 'Unauthorized'});
    }
    return schema.users.findBy({name});
});
```

## Create the acceptance tests

Considering we have the component logic ready to display some sort of element with an error selector if the service returns an error or
redirect to the index route if it went through, we can create an acceptance test like this:

```js
import { test } from 'qunit';

import moduleForAcceptance from 'erudite-battles-client/tests/helpers/module-for-acceptance';

moduleForAcceptance('Acceptance | login');

test('visiting /login', function(assert) {
  server.create('user');
  visit('/users/create');

  andThen(function() {
    assert.equal(currentURL(), '/users/create');
    fillIn('input.login-input', 'Faker');
    click('button.login-btn');
    // little hack to ensure rerender
    visit('/users/create');
    andThen(function() {
        assert.equal(find('div.alert-danger').text().trim(), 'User not found.');
    });
  });
});

```
