# @taktikorg/a-voluptatibus-consequatur <sup>[![Version Badge][npm-version-svg]][package-url]</sup>

[![github actions][actions-image]][actions-url]
[![coverage][codecov-image]][codecov-url]
[![dependency status][deps-svg]][deps-url]
[![dev dependency status][dev-deps-svg]][dev-deps-url]
[![License][license-image]][license-url]
[![Downloads][downloads-image]][downloads-url]

[![npm badge][npm-badge-png]][package-url]

An ES5 mostly-spec-compliant `Object.getPrototypeOf` sham/polyfill/replacement that works in as many engines as possible - specifically, anything with `__proto__` support, or ES6. Built-in types will also work correctly in older engines.

This package implements the [es-shim API](https://github.com/es-shims/api) interface. It works in an ES3-supported environment and complies with the [spec](https://www.ecma-international.org/ecma-262/5.1/).

## Example

```js
var getPrototypeOf = require('@taktikorg/a-voluptatibus-consequatur');
var assert = require('assert');

assert.equal(getPrototypeOf(true), Boolean.prototype);
assert.equal(getPrototypeOf(42), Number.prototype);
assert.equal(getPrototypeOf(''), String.prototype);
assert.equal(getPrototypeOf(/a/g), RegExp.prototype);
assert.equal(getPrototypeOf(new Date()), Date.prototype);
assert.equal(getPrototypeOf(function () {}), Function.prototype);
assert.equal(getPrototypeOf([]), Array.prototype);
assert.equal(getPrototypeOf({}), Object.prototype);
```

```js
var getPrototypeOf = require('@taktikorg/a-voluptatibus-consequatur');
var assert = require('assert');
/* when Object.getPrototypeOf is not present */
delete Object.getPrototypeOf;
var shimmed = getPrototypeOf.shim();
assert.equal(shimmed, getPrototypeOf.getPolyfill());

assert.equal(Object.getPrototypeOf(true), Boolean.prototype);
assert.equal(Object.getPrototypeOf(42), Number.prototype);
assert.equal(Object.getPrototypeOf(''), String.prototype);
assert.equal(Object.getPrototypeOf(/a/g), RegExp.prototype);
assert.equal(Object.getPrototypeOf(new Date()), Date.prototype);
assert.equal(Object.getPrototypeOf(function () {}), Function.prototype);
assert.equal(Object.getPrototypeOf([]), Array.prototype);
assert.equal(Object.getPrototypeOf({}), Object.prototype);
```

```js
var getPrototypeOf = require('@taktikorg/a-voluptatibus-consequatur');
var assert = require('assert');
/* when Object.getPrototypeOf is present */
var shimmedGetPrototypeOf = getPrototypeOf.shim();
assert.equal(shimmedGetPrototypeOf, Object.getPrototypeOf);
assert.equal(Object.getPrototypeOf([]), Array.prototype);
```

## Tests
Simply clone the repo, `npm install`, and run `npm test`

[package-url]: https://npmjs.org/package/@taktikorg/a-voluptatibus-consequatur
[npm-version-svg]: https://versionbadg.es/taktikorg/a-voluptatibus-consequatur.svg
[deps-svg]: https://david-dm.org/taktikorg/a-voluptatibus-consequatur.svg
[deps-url]: https://david-dm.org/taktikorg/a-voluptatibus-consequatur
[dev-deps-svg]: https://david-dm.org/taktikorg/a-voluptatibus-consequatur/dev-status.svg
[dev-deps-url]: https://david-dm.org/taktikorg/a-voluptatibus-consequatur#info=devDependencies
[npm-badge-png]: https://nodei.co/npm/@taktikorg/a-voluptatibus-consequatur.png?downloads=true&stars=true
[license-image]: https://img.shields.io/npm/l/@taktikorg/a-voluptatibus-consequatur.svg
[license-url]: LICENSE
[downloads-image]: https://img.shields.io/npm/dm/@taktikorg/a-voluptatibus-consequatur.svg
[downloads-url]: https://npm-stat.com/charts.html?package=@taktikorg/a-voluptatibus-consequatur
[codecov-image]: https://codecov.io/gh/taktikorg/a-voluptatibus-consequatur/branch/main/graphs/badge.svg
[codecov-url]: https://app.codecov.io/gh/taktikorg/a-voluptatibus-consequatur/
[actions-image]: https://img.shields.io/endpoint?url=https://github-actions-badge-u3jn4tfpocch.runkit.sh/taktikorg/a-voluptatibus-consequatur
[actions-url]: https://github.com/taktikorg/a-voluptatibus-consequatur/actions
