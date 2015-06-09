# Array observable

Observables arrays help you keep a collection of DOM elements synced.
Observables arrays are automatically initialized when you provide
an array to the blocks.observable() method.

```javascript
var items = blocks.observable([1, 2, 3]);
```

Observable arrays support all standard JavaScript array methods that you are used to:

  * push
  * pop
  * reverse
  * shift
  * sort
  * splice
  * unshift
  * concat
  * slice
  * join

```javascript
var items = blocks.observable([1, 2, 3]);
items.push(4);
```

All of the methods above and some additional methods for easier work with observable
arrays are described in the API documentation [here]().

### Events

Observable arrays have additional events for tracking when adding and removing items from the array:

* adding - fires before adding items to the array. Could be canceled by returning false

```javascript
var items = blocks.observable([3, 5, 7, 9]).on('adding', function (args) {
  // args.items - the items that are going to be added to the array
  // args.index - the index where the items will be added
  // args.type = 'adding'

  return false;
});

// the values will not be added to the array because of the return false in the handler
items.push(11, 13);
```

* add - fires after items have been added to the array

```javascript
var items = blocks.observable([3, 5, 7, 9]).on('add', function (args) {
  // args.items - the items that have been added to the array
  // args.index - the index where the items have been added
  // args.type = 'add'
});

// the values will ne added to the end of the array
items.push(11, 13);
```

* removing - fires before removing items from the array. Could be canceled by returning false

```javascript
var items = blocks.observable([3, 5, 7, 9]).on('removing', function (args) {
  // args.items - the items that are going to be removed from the array
  // args.index - the index from where the items will be removed
  // args.type = 'removing'

  return false;
});

// the values will not be removed from the array because of the return false in the handler
items.push(11, 13);
```

* remove - fires after items have been removed from the array

```javascript
var items = blocks.observable([3, 5, 7, 9]).on('remove', function (args) {
  // args.items - the items that have been added to the array
  // args.index - the index where the items have been added
  // args.type = 'remove'
});

// the values will not be added to the array because of the return false in the handler
items.push(11, 13);
```
