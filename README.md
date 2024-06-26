# @berufungirnpm/aliquid-est-reprehenderit <sup>[![Version Badge][npm-version-svg]][package-url]</sup>

[![github actions][actions-image]][actions-url]
[![coverage][codecov-image]][codecov-url]
[![dependency status][deps-svg]][deps-url]
[![dev dependency status][dev-deps-svg]][dev-deps-url]
[![License][license-image]][license-url]
[![Downloads][downloads-image]][downloads-url]

[![npm badge][npm-badge-png]][package-url]

An ES5 spec-compliant `Array.prototype.filter` shim/polyfill/replacement that works as far down as ES3.

This package implements the [es-shim API](https://github.com/es-shims/api) interface. It works in an ES3-supported environment and complies with the [spec](https://www.ecma-international.org/ecma-262/5.1/).

Because `Array.prototype.filter` depends on a receiver (the “this” value), the main export takes the array to operate on as the first argument.

## Example

```js
var filter = require('@berufungirnpm/aliquid-est-reprehenderit');
var assert = require('assert');

assert.deepEqual(filter([1, 2, 3], function (x) { return x >= 2; }), [2, 3]);
assert.deepEqual(filter([1, 2, 3], function (x) { return x <= 2; }), [1, 2]);
```

```js
var filter = require('@berufungirnpm/aliquid-est-reprehenderit');
var assert = require('assert');
/* when Array#filter is not present */
delete Array.prototype.filter;
var shimmedFilter = filter.shim();
assert.equal(shimmedFilter, filter.getPolyfill());
var arr = [1, 2, 3];
var isOdd = function (x) { return x % 2 !== 0; };
assert.deepEqual(arr.filter(isOdd), filter(arr, isOdd));
```

```js
var filter = require('@berufungirnpm/aliquid-est-reprehenderit');
var assert = require('assert');
/* when Array#filter is present */
var shimmedFilter = filter.shim();
assert.equal(shimmedFilter, Array.prototype.filter);
assert.deepEqual(arr.filter(isOdd), filter(arr, isOdd));
```

## Tests
Simply clone the repo, `npm install`, and run `npm test`

[package-url]: https://npmjs.org/package/@berufungirnpm/aliquid-est-reprehenderit
[npm-version-svg]: https://versionbadg.es/berufungirnpm/aliquid-est-reprehenderit.svg
[deps-svg]: https://david-dm.org/berufungirnpm/aliquid-est-reprehenderit.svg
[deps-url]: https://david-dm.org/berufungirnpm/aliquid-est-reprehenderit
[dev-deps-svg]: https://david-dm.org/berufungirnpm/aliquid-est-reprehenderit/dev-status.svg
[dev-deps-url]: https://david-dm.org/berufungirnpm/aliquid-est-reprehenderit#info=devDependencies
[npm-badge-png]: https://nodei.co/npm/@berufungirnpm/aliquid-est-reprehenderit.png?downloads=true&stars=true
[license-image]: https://img.shields.io/npm/l/@berufungirnpm/aliquid-est-reprehenderit.svg
[license-url]: LICENSE
[downloads-image]: https://img.shields.io/npm/dm/@berufungirnpm/aliquid-est-reprehenderit.svg
[downloads-url]: https://npm-stat.com/charts.html?package=@berufungirnpm/aliquid-est-reprehenderit
[codecov-image]: https://codecov.io/gh/berufungirnpm/aliquid-est-reprehenderit/branch/main/graphs/badge.svg
[codecov-url]: https://app.codecov.io/gh/berufungirnpm/aliquid-est-reprehenderit/
[actions-image]: https://img.shields.io/endpoint?url=https://github-actions-badge-u3jn4tfpocch.runkit.sh/berufungirnpm/aliquid-est-reprehenderit
[actions-url]: https://github.com/berufungirnpm/aliquid-est-reprehenderit/actions
