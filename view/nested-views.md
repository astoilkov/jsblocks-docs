# Nested Views

While your application grows you will want to keep with that demand and do not compromise on your architecture and code maintainability. This is where nested views come in handy.

```javascript
var App = blocks.Application();

App.View('Blog', {

});

// creating a nested view
// first parameter is the parent view
// second parameter is the new nested view name
App.View('Blog', 'Navigation', {

  // defining a message for the navigation
  helloMessage: 'Hello from Navigation'
});

// creating a nested view
// first parameter is the parent view
// second parameter is the new nested view name
App.View('Blog', 'Articles', {

  // defining a message for the articles
  helloMessage: 'Hello from Articles'
});

```

```html
<div data-query="view(Blog)">
  <div data-query="view(Navigation)">
    {{helloMessage}}
  </div>
  <div data-query="view(Articles)">
    {{helloMessage}}
  </div>
</div>
```
