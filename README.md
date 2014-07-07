# conda-js

A library to interact with `conda` from both the browser and Node.js

## Usage as a Library

From Node.js:

    $ npm install

Then, in your code, use

    conda = require('conda');

From the browser, include the Promise polyfill

    <script src="https://www.promisejs.org/polyfills/promise-4.0.0.js"></script>

as well as jQuery, and then include `conda.js`.


In your code use Conda like so:

    conda.info().then(function(info) {
        // Do something with info
    });

The library is structured asynchronously. Under Node.js `conda-js` calls
Conda as a subprocess with the `--json` option. In the browser, `conda-js`
makes a request to the server, which should use the subprocess as well.

## Development Server

To make the library easier to debug, it comes with its own server. Simply
run

    $ node conda.js --server

and visit [http://localhost:8080](http://localhost:8080). Open up the
JavaScript console:

    > conda.DEV_SERVER = true;

Now any further calls to `conda` methods will send the server the `conda`
command to run, enabling all of them to work without an actual server
implementation.
