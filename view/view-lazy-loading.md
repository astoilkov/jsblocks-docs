# View - lazy loading

Lazy loading of views are a must when building more complex pages for two reasons:
 * Improve performance because by default they are requested only when needed
 * Improve code architecture and maintainability by extracting HTML in different files

```javascript
var App = blocks.Application();

App.View('Documentation', {
  options: {
    // the url property points to the HTML file where the view is located
    url: 'views/documentation.html'
  }
});
```

## Preloading

When specifying an url for a view by default they are requested only when needed.
Use the preload property to load the content on page load instead of waiting until is needed.

```javascript
var App = blocks.Application();

App.View('Documentation', {
  options: {
    url: 'views/documentation.html',

    // this will force the view to be cached when the page loads
    preload: true
  }
});
```
