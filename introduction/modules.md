## Modules

jsblocks framework is constructed from three main modules that could be selectively excluded when downloading the framework if you don't need them:

 * **blocks.query** - DOM manipulation module that executes all *data-query* attributes when **blocks.query()** is called
   ```html
   <script>
   blocks.query({
      name: blocks.observable()
   });
   </script>
   <input data-query="val(name)" />
   <h1>My name is {{name}}!</h1>
   ```

 * **blocks.Application** - MVC(Model-View-Collection) module for creating scalable and maintainable applications. A layer on top of **blocks.query**
   ```javascript
   var App = blocks.Application();

   App.Model('Article', {
      content: App.Property()
   });

   App.Collection('Article', {
      options: {
        read: {
          url: 'service/articles'
        }
      }
   });

   App.View('Articles', {
      init: function () {
        this.articles = App.Collection.Articles();
      }
   });
   ```

 * **blocks.jsvalue** - entire library maintained by the jsblocks team inserted in the jsblocks framework as a convenience to work with data easily
   ```javascript
   var data = [4, 7, 1, 5, 10, 6, 3];

   // the result will be 'odd'
   var isEvenOrOddMore = blocks(data).filter(function (value) {
      return value < 10;
   }).map(function (value) {
      return value % 2 == 0 ? 'odd' : 'even'
   }).max().value();
   ```
