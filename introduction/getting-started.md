# Getting started

Just copy the HTML below and run it. Now you have your first working example build with jsblocks.

```html
<html>
  <head>
    <script src="http://jsblocks.com/jsblocks/blocks.js"></script>
    <script>
      blocks.query({
        name: blocks.observable()
      });
    </script>
  </head>
  <body>
    Name: <input placeholder="Enter your name" data-query="val(name)" />
    <h1>Hello, my name is {{name}}!</h1>
  </body>
</html>
```

## Basic concepts

 * Use [`blocks.query()`](../api.md#blocks-query ) method and pass an object which could be accessed in the HTML. Calling the method executes all data-query attributes and {{expressions}}

   ```javascript
   blocks.query({
     type: 'firstName',
     name: 'John Doe'
   });
   ```

 * [`data-query`](../syntax/data-query-syntax.md) attribute on a element is used to call query methods. Syntax is the same as calling a method in JavaScript with support for chaining

   ```html
   <input data-query="val(name).setClass(type)" />
   <div data-query="setClass(type)" />
   ```

 * [`{{expressions}}`](../syntax/expressions-syntax.md) are used to render a value from the model into the DOM

   ```html
   <input class="{{type}}" />
   <h2>{{name}}</h2>
   ```

 * [`blocks.observable()`](../working-with-observables/introduction.md) is the object you create when you need a value that will be always synced in the model and in the DOM

   ```javascript
   blocks.query({
     // the value will be always in sync with the DOM and vice versa
     name: blocks.observable('John Doe')
   });
   ```

 * Use [`blocks.Application`](../mvc/introduction.md) and its MVC(Model-View-Collection) structure to create better architecture and maintainability for your application

   ```javascript
   var App = blocks.Application();

   // create Models, Collections and Views here
   ```