# Dependency observable

Dependency observables make it easy to automatically update observable which is constructed from another observable. Let's take a look at examples with the two types of dependency observables.

## Read-only dependency observable

Read only dependency observables are created by providing a function to the `blocks.observable()` method. The framework will automatically detect which observables are used by immediately calling the function.

```javascript
var firstName = blocks.observable('John');
var lastName = blocks.observable('Doe');
var fullName = blocks.observable(function () {
  return firstName() + ' ' + lastName();
});
```

## Read-write dependency observable

There are some cases when you need a read\write dependency observable
to control more complex scenarios. You could create such an observable
by passing an object with `get()` and `set()` methods to the `blocks.observable()` method.

```javascript
var firstName = blocks.observable('John');
var lastName = blocks.observable('Doe');
var fullName = blocks.observable({
  get: function () {
    return firstName() + ' ' + lastName();
  },

  set: function (value) {
    var splits = value.split(' ');
    firstName(value[0]);
    lastName(value[1]);
  }
});
```
