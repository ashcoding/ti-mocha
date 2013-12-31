# ti-mocha [![Build Status](https://travis-ci.org/tonylukasavage/ti-mocha.png?branch=master)](https://travis-ci.org/tonylukasavage/ti-mocha) [![Built with Grunt](https://cdn.gruntjs.com/builtwith.png)](http://gruntjs.com/)

Simple and reliable support for [mocha](https://github.com/visionmedia/mocha) testing with Appcelerator's [Titanium](http://www.appcelerator.com/titanium/) SDK.

ti-mocha takes mocha's existing browser-compatible build, makes a few Titanium-specific modifications, adds a Titanium compatible reporter, and it's good to go. The goal is to make the modifications to mocha as minimal as possible in order to make maintaining ti-mocha's stability and version parity very easy. It also works well with the browser-compatible version of the [should.js](https://github.com/visionmedia/should.js) assertion library.

Check out [mocha's documentation](http://visionmedia.github.io/mocha/) for more details.

## Installation

1. Download [ti-mocha.js](https://raw.github.com/tonylukasavage/ti-mocha/master/ti-mocha.js).
2. Copy `ti-mocha.js` into your project's `Resources` folder.
3. `require('ti-mocha')` in your app.js to make `mocha` available globally.

## Example

```javascript
// require ti-mocha
require('ti-mocha');

// setup the UI and the reporter
mocha.setup({
	ui: 'bdd',
	reporter: 'ti-spec'
});

// create the test suite
describe('ti-mocha', function() {

	describe('suite 1', function() {

		it('shows passing tests (fast)', function(){});

		it('shows passing tests (slow)', function(done){
			setTimeout(done, 1500);
		});

	});

	describe('suite 2', function() {

		it('shows pending tests');

		it('fails a test', function() {
			throw new Error('this shoud fail');
		});

	});

});

// run the tests
mocha.run();
```

## Development

1. Install [node.js]().
2. Install [grunt](): `sudo npm install -g grunt-cli`
3. `cd ti-mocha && npm install`

#### Build

```
grunt build
```

This process will generate a new `ti-mocha.js` file based on the files in `src`. See [lib/build.js](lib/build.js) for details of the simple build process.

#### Testing

```
grunt test
```

## Issues and Contributing

Distributed under [MIT License](LICENSE). Please report issues, new features/reporters, or requests in this repo's [issue tracker](https://github.com/tonylukasavage/ti-mocha/issues).

Bear in mind that this is a straight-up, minimal porting effort to make mocha work with Titanium. If you want additional features or functionality in mocha itself, please report them in the [mocha](https://github.com/visionmedia/mocha) repository.

## TODO

* Only tested in iOS simulator on Mac OSX so far. The code should be platform-agnostic, but it would be good to get some testing done on other mobile and host OSes.
* More robust testing for build script, should at least verify the validity of the resulting ti-mocha.js file.
