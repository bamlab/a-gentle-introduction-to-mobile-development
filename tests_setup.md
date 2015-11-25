# Set up your unit testing environment

## Libraries

To install the libraries for unit testing, paste this in your terminal:
````shell
npm install --save-dev karma karma-chrome-launcher karma-junit-reporter \
karma-mocha karma-mocha-reporter karma-phantomjs-launcher karma-sinon-chai \
chai mocha sinon karma-coffee-preprocessor karma-chai karma-sinon
```

## Config

Create `karma.js` and paste this:
```js
module.exports = function(config) {
  return config.set({
    basePath: '../',
    frameworks: ['mocha', 'chai', 'sinon'],
    files: [],
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
"test": "./node_modules/karma/bin/karma start test/karma.conf.coffee --single-run",
```