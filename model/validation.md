## Model validation

A Model manages all its Property objects and provide the `validate()` method and the `valid` and `validationErrors` observables.

```javascript
var App = blocks.Application();

var User = App.Model({
  username: App.Property({
    required: 'Username is required!'
  }),

  email: App.Property({
    email: 'Please provide a valid email!'
  })
});

var user = User({
  username: '',
  email: 'email@gmail'
});

// validate the username and email properties
user.validate();

// alerts 'false' (both username and email failed validation)
alert(user.valid());

// alerts 'Username is required!,Please provide a valid email!'
// validationErrors is an array of all validation error messages
// constructed from extracting the values from all properties errorMessages collection
alert(user.validationErrors());
```

> For more information about validation go [here](../property/validation.md).
