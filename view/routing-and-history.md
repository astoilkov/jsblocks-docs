# Routing

Routing is the soul of a single-page application. It let's you create pages that correspond to a particular URL(route) and are invisible until the corresponding route is hit.

Let's build an example that will have two pages - Home and Contacts.

```javascript
var App = blocks.Application();

App.View('Home', {
  // options object contains all properties that define the View behavior
  options: {
    // enabling the View routing and setting it to the root page
    // for a www.example.com the root is the same www.example.com
    route: '/'
  }
});

App.View('Contacts', {
  options: {
    // enabling the View routing and setting to a Contacts route
    // for a www.example.com the route will be found under www.example.com/#Contacts
    route: 'Contacts'
  },

  init: function () {

  }
});

App.View('Product', {
  options: {

    route: 'Product/{{type}}'
  },

  // callback called when the view have been successfully
  routed: function () {

  }
});
```

```html
<a href="#" data-query="navigateTo(Home)">Home</a>
<a href="#" data-query="navigateTo(Contacts)">Contact Us</a>

<div data-query="view(Home)">
  Home
</div>
<div data-query="view(Contacts)">
  Contacts
</div>
<div data-query="view(Product)">
  Product {{route.type}}
</div>
```

## Routes

```javascript

'/'

'Contacts'

'Product/{{type}}'

blocks.route('Product/{{type}}').optional('type')

```

## hash vs pushState history

jsblocks have two types of history management to best suite your needs. Both have advantages and disadvantages which are illustrated below:

### hash type history

**Pros:**
* Easy to use - does not require additional setup and is the default option
* Cross browser solution and consistent across users

**Cons:**
* Appends # to the end of the URL and could be not so intuitive for the end user
* As the server couldn't know about the #hash value it could not prerender the appropriate content and leaves the client code to  

### pushState history

```javascript
var App = blocks.Application({
  history: 'pushState'
});
```

**Pros:**
* It is harder to implement

**Cons:**
* Inconsistent behavior cross browsers
