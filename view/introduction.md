# View Introduction

Views are a way to divide your application into pieces. Often you will find out that views are most appropriate to represent entire pages in your application and [Nested Views](../view/nested-views.md) to be logic separation in your current view.

Let's take a look at a simple example.

```html
<script>
  var App = blocks.Application();

  App.View('HelloView', {
    helloMessage: 'Hello from View',

    // called when the view is created
    // do any initialization work here
    init: function () {
      this.description = 'I am powerful';
    }
  });
</script>
<div data-query="view(HelloView)">
  <h1>{{helloMessage}}</h1>
  <p>{{description}}</p>
</div>
```
> Views are most powerful when combined with [Models](../model/introduction.md) and [Collections](../collection/introduction.md).**
