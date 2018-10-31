# slugify [![Build Status](https://travis-ci.org/sindresorhus/slugify.svg?branch=master)](https://travis-ci.org/sindresorhus/slugify)

> Slugify a string

Useful for URLs, filenames, and IDs.

It correctly handles [German umlauts](https://en.wikipedia.org/wiki/Germanic_umlaut), Vietnamese, Arabic, Russian, and more.


## Install

```
$ npm install @sindresorhus/slugify
```


## Usage

```js
const slugify = require('@sindresorhus/slugify');

slugify('I ♥ Dogs');
//=> 'i-love-dogs'

slugify('  Déjà Vu!  ');
//=> 'deja-vu'

slugify('fooBar 123 $#%');
//=> 'foo-bar-123'

slugify('BAR and baz', {separator: '_'});
//=> 'bar_and_baz'

slugify('I ♥ 🦄 & 🐶', {
  customReplacements: [
    ['🐶', 'dog']
  ]
});
//=> 'i-love-unicorn-and-dog'

slugify('Déjà Vu!', {lowercase: false});
//=> 'Deja-Vu'
```

## API

### slugify(input, [options])

#### input

Type: `string`

#### options

Type: `Object`

##### separator

Type: `string`<br>
Default: `-`

##### customReplacements

Type: `Array`<br>
Default: `[
  ['&', ' and '],
  ['🦄', ' unicorn '],
  ['♥', ' love ']
]`

Specifying this only replaces the default if you set an item with the same key, like `&`. The replacements are run on the original string before any other transformations.

```js
slugify('Foo@unicorn', {
	customReplacements: [
		['@', 'at']
	]
});
//=> 'fooatunicorn'
```

Add a leading and trailing space to the replacement to have it separated by dashes:

```js
slugify('foo@unicorn', {
	customReplacements: [
		['@', ' at ']
	]
});
//=> 'foo-at-unicorn'
```

##### lowercase

Type: `Boolean`<br>
Default: `true`


## Related

- [slugify-cli](https://github.com/sindresorhus/slugify-cli) - CLI for this module
- [filenamify](https://github.com/sindresorhus/filenamify) - Convert a string to a valid safe filename


## License

MIT © [Sindre Sorhus](https://sindresorhus.com)
