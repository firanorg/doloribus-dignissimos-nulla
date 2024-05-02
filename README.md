# @firanorg/doloribus-dignissimos-nulla <sup>[![Version Badge][npm-version-svg]][package-url]</sup>

[![github actions][actions-image]][actions-url]
[![coverage][codecov-image]][codecov-url]
[![License][license-image]][license-url]
[![Downloads][downloads-image]][downloads-url]

[![npm badge][npm-badge-png]][package-url]

> Returns true if a value has the characteristics of a valid JavaScript data descriptor.

## Examples

`true` when the descriptor has valid properties with valid values.
`false` when not an object or when the object has invalid properties.

```js
var isDataDesc = require('@firanorg/doloribus-dignissimos-nulla');
var assert = require('assert');

assert.equal(true, isDataDesc({ value: 'foo' }));
assert.equal(true, isDataDesc({ value: function () {} }));
assert.equal(true, isDataDesc({ value: true }));

assert.equal(false, isDataDesc('a'));
assert.equal(false, isDataDesc(null));
assert.equal(false, isDataDesc([]));

assert.equal(false, isDataDesc({ value: 'foo', bar: 'baz' }));
assert.equal(false, isDataDesc({ value: 'foo', bar: 'baz' }));
assert.equal(false, isDataDesc({ value: 'foo', get: function () {} }));
assert.equal(false, isDataDesc({ get: function () {}, value: 'foo' }) );
 
assert.equal(false, isDataDesc({ value: 'foo', enumerable: 'foo' }));
assert.equal(false, isDataDesc({ value: 'foo', configurable: 'foo' }));
assert.equal(false, isDataDesc({ value: 'foo', writable: 'foo' }));
```

## Valid properties

The only valid data descriptor properties are the following:

* `configurable` (required)
* `enumerable` (required)
* `value` (optional)
* `writable` (optional)

To be a valid data descriptor, either `value` or `writable` must be defined.

**Invalid properties**

A descriptor may have additional _invalid_ properties (an error will **not** be thrown).

```js
var foo = {};

Object.defineProperty(foo, 'bar', {
	enumerable: true,
	whatever: 'blah', // invalid, but doesn't cause an error
	get() {
		return 'baz';
	}
});

assert.equal(foo.bar, 'baz');
```

### Related projects

* [is-accessor-descriptor](https://npmjs.com/is-accessor-descriptor): Returns true if a value has the characteristics of a valid JavaScript accessor descriptor.
* [is-descriptor](https://npmjs.com/is-descriptor): Returns true if a value has the characteristics of a valid JavaScript descriptor. Works for… [more](https://npmjs.com/is-descriptor)

## Tests

Simply clone the repo, `npm install`, and run `npm test`

[package-url]: https://npmjs.org/package/@firanorg/doloribus-dignissimos-nulla
[npm-version-svg]: https://versionbadg.es/inspect-js/@firanorg/doloribus-dignissimos-nulla.svg
[deps-svg]: https://david-dm.org/inspect-js/@firanorg/doloribus-dignissimos-nulla.svg
[deps-url]: https://david-dm.org/inspect-js/@firanorg/doloribus-dignissimos-nulla
[dev-deps-svg]: https://david-dm.org/inspect-js/@firanorg/doloribus-dignissimos-nulla/dev-status.svg
[dev-deps-url]: https://david-dm.org/inspect-js/@firanorg/doloribus-dignissimos-nulla#info=devDependencies
[npm-badge-png]: https://nodei.co/npm/@firanorg/doloribus-dignissimos-nulla.png?downloads=true&stars=true
[license-image]: https://img.shields.io/npm/l/@firanorg/doloribus-dignissimos-nulla.svg
[license-url]: LICENSE
[downloads-image]: https://img.shields.io/npm/dm/@firanorg/doloribus-dignissimos-nulla.svg
[downloads-url]: https://npm-stat.com/charts.html?package=@firanorg/doloribus-dignissimos-nulla
[codecov-image]: https://codecov.io/gh/inspect-js/@firanorg/doloribus-dignissimos-nulla/branch/main/graphs/badge.svg
[codecov-url]: https://app.codecov.io/gh/inspect-js/@firanorg/doloribus-dignissimos-nulla/
[actions-image]: https://img.shields.io/endpoint?url=https://github-actions-badge-u3jn4tfpocch.runkit.sh/inspect-js/@firanorg/doloribus-dignissimos-nulla
[actions-url]: https://github.com/firanorg/doloribus-dignissimos-nulla/actions
