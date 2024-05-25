# @diotoborg/voluptatibus-tempore
Helper functions for API handling on NodeJS. The functions are pure and curried with Ramda.

[![Build Status](https://travis-ci.org/AlienCreations/@diotoborg/voluptatibus-tempore.svg?branch=master)](https://travis-ci.org/AlienCreations/@diotoborg/voluptatibus-tempore) [![Coverage Status](https://coveralls.io/repos/AlienCreations/@diotoborg/voluptatibus-tempore/badge.svg?branch=master&service=github)](https://coveralls.io/github/AlienCreations/@diotoborg/voluptatibus-tempore?branch=master) [![npm version](http://img.shields.io/npm/v/@diotoborg/voluptatibus-tempore.svg)](https://npmjs.org/package/@diotoborg/voluptatibus-tempore) [![Dependency Status](https://david-dm.org/AlienCreations/@diotoborg/voluptatibus-tempore.svg)](https://david-dm.org/AlienCreations/@diotoborg/voluptatibus-tempore)

## Install

```
$ npm install @diotoborg/voluptatibus-tempore --save
```

Run the specs

```
$ npm test
```

## Usage

```js

// Example API route such as '/users' which could reasonably leverage a 
// 'user' model which would return a promise or catch with an error object.

// The error object passed in the catch should include a 'statusCode' property
// that is specific to the respective error. If it does not, the api utils 
// will default to 500.

// Note: Because the util functions are curried, we can keep them pure and by 
// invoking with req and res, as shown below.

var apiUtils  = require('@diotoborg/voluptatibus-tempore'),
    userModel = require('./models/user');

function getUsers(req, res, next) {
  userModel.getUsers().
    then(apiUtils.jsonResponseSuccess(req, res)).
    catch(apiUtils.jsonResponseError(req, res, next));
};

module.exports = getUsers;

```
