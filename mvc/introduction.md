## MVC(Model-View-Collection) Introduction

So it's time to understand the jsblocks MVC(Model-View-Collection) part and how to build complex applications with solid architecture. jsblocks MVC is a module and it is not mandatory to build your applications with it. However, it is designed in such a way that you just won't ever need anything else. So let's see it in action.

Creating a jsblocks MVC Application is as easy as calling the blocks.Application method which creates a new Application instance.

```javascript
// creating a new application
// calling the blocks.Application() method multiple times returns the same application instance so you could access it in different files
var App = blocks.Application();

// create your views, models and collections here
```

Below is an example build with the MVC module. For additional information you could follow the corresponding documentation for views, models and collections.
* [Views - Introduction](../views/introduction.md)
* [Models - Introduction](../models/introduction.md)
* [Collections - Introduction](../collections/introduction.md)

```javascript
var App = blocks.Application();

// place methods and values directly on the application object by using the extend() method
App.extend({
  helloMessage: 'Hello from jsblocks MVC'
});

var Article = App.Model({
  content: App.Property({
    defaultValue: 'no content'
  })
});

var Articles = App.Collection(Article, {
  // place your collection methods here
});

var Profile = App.Model({
  // observable property with required validation
  username: App.Property({
    required: true
  }),

  // observable property with email validation
  email: App.Property({
    email: true
  })
});

App.View('SignUp', {
  articles: Articles([{
    content: 'first article'
  }, {
    content: 'second article'
  }, {
    // no article content so the defaultValue 'no content' will be applied
  }]),

  profile: Profile()
});
```

```html
<h1>{{helloMessage}}</h1>
<div data-query="view(SignUp)">
    <div data-query="with(profile)">
        <input placeholder="username" data-query="val(username)">
        <span data-query="visible(!username.valid()).html(username.errorMessage)"></span>
        <input placeholder="email" data-query="val(email)">
        <span data-query="visible(!email.valid()).html(email.errorMessage)"></span>
    </div>
    <h3>Articles from other users</h3>
    <ul data-query="each(articles)">
        <li>{{content}}</li>
    </ul>
</div>
```
