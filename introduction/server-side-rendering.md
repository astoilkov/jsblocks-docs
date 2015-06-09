# Server-side rendering

## Getting started

Download the [jsblocks-seed](https://github.com/astoilkov/jsblocks-seed) project and run the commands below:

```javascript
npm install

npm run node
```

## Understanding server-side rendering basics

Creating a `blocks.server()` does couple of things:
 * creates an express app listening to the specified port (default 8000)
 * expects an `app` folder where to place `index.html` file which will be the main application view
 * register a middleware which handles all requests and servers all routes that you have created in your client-side code
 * when a route is satisfied it renders the page executing your client-side application logic on the server

```javascript
var blocks = require('blocks');

// creates the server which will automatically handle server-side rendering
blocks.server();
```

## `blocks.server()`

```javascript
var blocks = require('blocks');
var server = blocks.server({
    // the port at which your application will be run
    port: 8000,

    // the folder where your application files like .html, .js and .css are going to be
    // the value is passed to express.static() middleware
    static: 'app',

    // caches pages result instead of executing them each time
    // disabling cache could impact performance
    cache: true,

    // provide an express middleware function or an array of middleware functions
    // use: [compression(), bodyParser()]
    use: null
});

// returns the `express` app `blocks.server` is using internally
var app = server.express();
```