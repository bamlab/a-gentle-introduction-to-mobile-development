# Set up your unit testing environment

## Libraries

To install the libraries for unit testing, paste this in your terminal:

````shell
npm install --save-dev karma karma-chrome-launcher karma-junit-reporter \
karma-mocha karma-mocha-reporter karma-phantomjs-launcher karma-sinon-chai \
chai mocha sinon karma-coffee-preprocessor karma-chai karma-sinon
```

## Config

Create `test/karma.conf.js` and paste this:

```js
module.exports = function(config) {
  return config.set({
    basePath: '../',
    frameworks: ['mocha', 'chai', 'sinon'],
    files: [
        // put your librairies files here, e.g.
        'www/lib/**/*.js',
        // and your tests (here tests are the files that are in 'test'
        // folder and finish by .spec.js), e.g.
        'test/**/*.spec.js', 
    ],
    exclude: [],
    reporters: ['progress'],
    port: 9876,
    colors: true,
    logLevel: config.LOG_INFO,
    autoWatch: true,
    browsers: ['Chrome'],
    singleRun: true
  });
};
```

Add in your `package.json` in `scripts`section:

```
"test": "./node_modules/karma/bin/karma start test/karma.conf.js --single-run",
```

# Run your first test

Write in a new file for your test, for instance `test/dummy.spec.js`:
```js
var expect = chai.expect;
describe('Dummy test', function() {
  return it('should crash', function() {
    return expect(true).to.be.false;
  });
});
```

Now, type `npm test` in your terminal and you should see that 0 of 1 test passed. To fix the test, change false in true and re-run the test, now 1 of 1 test passed.
