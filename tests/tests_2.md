# How to write a simple test ?

Imagine you write a fibonacci function, e.g. in `fib.js`:
```js
function fib(n) {
	if (n <= 1) {
		return 1;
	}
	return fib(n - 1) + fib(n - 2);
}
```

And you want to test it.

Firstly, you can write a file `fib.spec.js`.

In the karma config file, import the fib function and the test:
```js
files: [
	'fib.js',
	'test/fib.spec.js',
],
```

At the top of the test file, you can alias the `expect`:
```js
var expect = chai.expect;
```

Then describe what you want to test:
```js
describe('fibonacci function', function() {
	// your tests will be here
});
```

Inside, you can write tests. A test has a description of what it tests, you write it beginning by 'it should do something', e.g. :
```js
describe('fibonacci function', function() {
	it('should return 1 when param is 1', function() {
		// your test
	});

	// other tests about fibonacci function
});
```

The principle of a test is to execute some code and then make some assertions about the results.
Chai is the library that provide us the assertions method and it has 3 styles to write assertions :
* assert, e.g. : assert.equal(foo, 'bar');
* expect, e.g. : expect(foo).to.equal('bar');
* should, e.g. : foo.should.equal('bar');

The three syntax have the same features, the difference is only visual.

At BAM, we usually write tests with the 'expect' syntax:

```js
describe('fibonacci function', function() {
	it('should return 1 when param is 1', function() {
		expect(fib(1)).to.equal(1);
	});
});
```

And you can write a few other tests:
```js
describe('fibonacci function', function() {
	it('should return 1 when param is 1', function() {
		expect(fib(1)).to.equal(1);
	});

	it('should return 1 when param is 0', function() {
		expect(fib(0)).to.equal(1);
	});

	it('should return 2 when param is 2', function() {
		expect(fib(2)).to.equal(2);
	});
});
```
