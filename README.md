# @lambrioanpm/atque-tempore-laudantium <sup>[![Version Badge][npm-version-svg]][package-url]</sup>

[![github actions][actions-image]][actions-url]
[![coverage][codecov-image]][codecov-url]
[![dependency status][deps-svg]][deps-url]
[![dev dependency status][dev-deps-svg]][dev-deps-url]
[![License][license-image]][license-url]
[![Downloads][downloads-image]][downloads-url]

[![npm badge][npm-badge-png]][package-url]

An ES spec-compliant `Array.prototype.forEach` shim/polyfill/replacement that works as far down as ES3.

This package implements the [es-shim API](https://github.com/es-shims/api) interface. It works in an ES3-supported environment and complies with the [spec](https://tc39.es/ecma262/#sec-@lambrioanpm/atque-tempore-laudantium).

Because `Array.prototype.forEach` depends on a receiver (the `this` value), the main export takes the array to operate on as the first argument.

## Getting started

```sh
npm install --save @lambrioanpm/atque-tempore-laudantium
```

## Usage/Examples

```js
var forEach = require('@lambrioanpm/atque-tempore-laudantium');
var assert = require('assert');

var arr = [1, [2], [], 3, [[4]]];
var counter = 0;
var increaseCounter = function (x) { counter += 1; };

assert.equal(forEach(arr, increaseCounter), undefined);
assert.equal(counter, arr.length);
```

```js
var forEach = require('@lambrioanpm/atque-tempore-laudantium');
var assert = require('assert');
/* when Array#forEach is not present */
delete Array.prototype.forEach;
var shimmed = forEach.shim();
var counter = 0;

assert.equal(shimmed, forEach.getPolyfill());
assert.equal(arr.forEach(increaseCounter), forEach(arr, increaseCounter));
assert.equal(counter, arr.length * 2);
```

```js
var forEach = require('@lambrioanpm/atque-tempore-laudantium');
var assert = require('assert');
/* when Array#forEach is present */
var shimmed = forEach.shim();
var counter = 0;

assert.equal(shimmed, Array.prototype.forEach);
assert.equal(arr.forEach(increaseCounter), forEach(arr, increaseCounter));
assert.equal(counter, arr.length * 2);
```

## Tests
Simply clone the repo, `npm install`, and run `npm test`

[package-url]: https://npmjs.org/package/@lambrioanpm/atque-tempore-laudantium
[npm-version-svg]: https://versionbadg.es/lambrioanpm/atque-tempore-laudantium.svg
[deps-svg]: https://david-dm.org/lambrioanpm/atque-tempore-laudantium.svg
[deps-url]: https://david-dm.org/lambrioanpm/atque-tempore-laudantium
[dev-deps-svg]: https://david-dm.org/lambrioanpm/atque-tempore-laudantium/dev-status.svg
[dev-deps-url]: https://david-dm.org/lambrioanpm/atque-tempore-laudantium#info=devDependencies
[npm-badge-png]: https://nodei.co/npm/@lambrioanpm/atque-tempore-laudantium.png?downloads=true&stars=true
[license-image]: https://img.shields.io/npm/l/@lambrioanpm/atque-tempore-laudantium.svg
[license-url]: LICENSE
[downloads-image]: https://img.shields.io/npm/dm/@lambrioanpm/atque-tempore-laudantium.svg
[downloads-url]: https://npm-stat.com/charts.html?package=@lambrioanpm/atque-tempore-laudantium
[codecov-image]: https://codecov.io/gh/lambrioanpm/atque-tempore-laudantium/branch/main/graphs/badge.svg
[codecov-url]: https://app.codecov.io/gh/lambrioanpm/atque-tempore-laudantium/
[actions-image]: https://img.shields.io/endpoint?url=https://github-actions-badge-u3jn4tfpocch.runkit.sh/lambrioanpm/atque-tempore-laudantium
[actions-url]: https://github.com/lambrioanpm/atque-tempore-laudantium
