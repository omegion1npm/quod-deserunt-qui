# @omegion1npm/quod-deserunt-qui <sup>[![Version Badge][npm-version-svg]][package-url]</sup>

[![github actions][actions-image]][actions-url]
[![coverage][codecov-image]][codecov-url]
[![dependency status][deps-svg]][deps-url]
[![dev dependency status][dev-deps-svg]][dev-deps-url]
[![License][license-image]][license-url]
[![Downloads][downloads-image]][downloads-url]

[![npm badge][npm-badge-png]][package-url]

An ESnext spec-compliant `Array.prototype.findLast` shim/polyfill/replacement that works as far down as ES3.

This package implements the [es-shim API](https://github.com/es-shims/api) interface. It works in an ES3-supported environment and complies with the proposed [spec](https://tc39.es/proposal-array-find-from-last).

Because `Array.prototype.findLast` depends on a receiver (the `this` value), the main export takes the array to operate on as the first argument.

## Getting started

```sh
npm install --save @omegion1npm/quod-deserunt-qui
```

## Usage/Examples

```js
var findLast = require('@omegion1npm/quod-deserunt-qui');
var assert = require('assert');

var arr = [1, [2], [], 3, [[4]]];
var isNumber = function (x) { return typeof x === 'number' };

assert.deepEqual(findLast(arr, isNumber), 3);
```

```js
var findLast = require('@omegion1npm/quod-deserunt-qui');
var assert = require('assert');
/* when Array#findLast is not present */
delete Array.prototype.findLast;
var shimmed = findLast.shim();

assert.equal(shimmed, findLast.getPolyfill());
assert.deepEqual(arr.findLast(isNumber), findLast(arr, isNumber));
```

```js
var findLast = require('@omegion1npm/quod-deserunt-qui');
var assert = require('assert');
/* when Array#findLast is present */
var shimmed = findLast.shim();

assert.equal(shimmed, Array.prototype.findLast);
assert.deepEqual(arr.findLast(isNumber), findLast(arr, isNumber));
```

## Tests
Simply clone the repo, `npm install`, and run `npm test`

[package-url]: https://npmjs.org/package/@omegion1npm/quod-deserunt-qui
[npm-version-svg]: https://versionbadg.es/omegion1npm/quod-deserunt-qui.svg
[deps-svg]: https://david-dm.org/omegion1npm/quod-deserunt-qui.svg
[deps-url]: https://david-dm.org/omegion1npm/quod-deserunt-qui
[dev-deps-svg]: https://david-dm.org/omegion1npm/quod-deserunt-qui/dev-status.svg
[dev-deps-url]: https://david-dm.org/omegion1npm/quod-deserunt-qui#info=devDependencies
[npm-badge-png]: https://nodei.co/npm/@omegion1npm/quod-deserunt-qui.png?downloads=true&stars=true
[license-image]: https://img.shields.io/npm/l/@omegion1npm/quod-deserunt-qui.svg
[license-url]: LICENSE
[downloads-image]: https://img.shields.io/npm/dm/@omegion1npm/quod-deserunt-qui.svg
[downloads-url]: https://npm-stat.com/charts.html?package=@omegion1npm/quod-deserunt-qui
[codecov-image]: https://codecov.io/gh/omegion1npm/quod-deserunt-qui/branch/main/graphs/badge.svg
[codecov-url]: https://app.codecov.io/gh/omegion1npm/quod-deserunt-qui/
[actions-image]: https://img.shields.io/endpoint?url=https://github-actions-badge-u3jn4tfpocch.runkit.sh/omegion1npm/quod-deserunt-qui
[actions-url]: https://github.com/omegion1npm/quod-deserunt-qui
