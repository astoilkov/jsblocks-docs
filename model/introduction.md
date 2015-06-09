# Models

Models are a way to represent a single item in your View. They are useful because their code logic could be reused multiple times and you could achieve validation and custom formatting of your values.

```javascript
var App = blocks.Application();

// creating a new Model type
var User = App.Model({
  // called when the Model is created
  init: function () {
    // do any initialization work here
  },

  firstName: blocks.observable(),

  lastName: blocks.observable(),

  // defining a dependency observable that returns the full name of the user
  fullName: blocks.observable(function() {
    return this.firstName() + ' ' + this.lastName();
  })
});

App.View('Profile', {
  profile: User({
    firstName: 'John',
    lastName: 'Doe'
  })
});
```

```html
<div data-query="view(Profile)">
  <h2>Welcome, {{profile.fullName}}!</h2>
  First Name: <input data-query="val(profile.firstName)" />
  <br />
  Last Name: <input data-query="val(profile.lastName)" />
</div>
```
