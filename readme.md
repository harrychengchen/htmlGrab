
###Browser compatibility###

The script should work fine on the following browsers:

* Firefox 3.5+
* Google Chrome
* Opera 12+
* IE9+
* Safari 6+

As each CSS property needs to be manually built to be supported, there are a number of properties that are not yet supported.

### Usage ###

**Note!** These instructions are for using the current dev version of 0.5, for the latest release version (0.4.1), checkout the [old readme](https://github.com/niklasvh/html2canvas/blob/v0.4/readme.md).

To render an `element` with html2canvas, simply call:
` html2canvas(element[, options]);`

The function returns a [Promise](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise) containing the `<canvas>` element. Simply add a promise fullfillment handler to the promise using `then`:

    html2canvas(document.body).then(function(canvas) {
        document.body.appendChild(canvas);
    });

### Building ###

Install Grunt and uglifyjs:

    $ npm install -g grunt-cli uglify-js

Run the full build process (including lint, qunit and webdriver tests):

    $ grunt

Skip lint and tests and simply build from source:

    $ grunt build

### Running tests ###

The library has two sets of tests. The first set is a number of qunit tests that check that different values parsed by browsers are correctly converted in html2canvas. To run these tests with grunt you'll need [phantomjs](http://phantomjs.org/).

The other set of tests run Firefox, Chrome and Internet Explorer with [webdriver](https://github.com/niklasvh/webdriver.js). The selenium standalone server (runs on Java) is required for these tests and can be downloaded from [here](http://code.google.com/p/selenium/downloads/list). They capture an actual screenshot from the test pages and compare the image to the screenshot created by html2canvas and calculate the percentage differences. These tests generally aren't expected to provide 100% matches, but while commiting changes, these should generally not go decrease from the baseline values.

Start by downloading the dependencies:

    $ npm install

Run qunit tests:

    $ grunt test

