# Property

Property is a way to define value in a model or in a collection and they convert to an observable so everything that could be done on an observable could be applied to a property. Let's see an example.

> Note: Property have advantages over an observable which are described [here](../property/options.md)

**Here is the implementation using an observable**
```javascript
var features = blocks.observable([]).extend('filter', function (value) {
  return value.type == 'feature';
});
```

**Here is the equivalent when using Property**
```javascript
var App = blocks.Application();

var Project = App.Model({
  features: App.Property({
    
  }).extend('filter', function (value) {
    return value.type == 'feature';
  })
});
```
