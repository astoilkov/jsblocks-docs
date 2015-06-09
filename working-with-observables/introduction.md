# Observable introduction

Observables are the way to achieve two-way data binding.
When an observable value is changed the DOM updates and vice versa.

```javascript
function Model() {
  this.firstName = blocks.observable('John');
  this.lastName = blocks.observable('Doe');
  this.age = blocks.observable('23');

  this.fullName = blocks.observable(function () {
    return this.firstName() + ' ' + this.lastName();
  }, this);
}

blocks.query(new Model());
```

```html
<div>
  My name is {{firstName}} {{lastName}} and I am {{age}} years old.
</div>
<div>
  My name is {{fullName}} and I am {{age}} years old.
</div>
<h2>
Change name  
</h2>
FirsName: <input data-query="val(firstName)" />
<br />
Last Name: <input data-query="val(lastName)" />
<br />
Age: <input data-query="val(age)" />
```

The most commonly used observable is the one that is created when you provide a primitive value or an object to the `blocks.observable()` method.

```javascript
var fullName = blocks.observable('My name');
```

Accessing the observable value is as easy as calling a function.
Regardless in code or in the HTML.

```javascript
var firstName = blocks.observable('John');
alert('My name is ' + firstName());
```

```html
<script>
  blocks.query({
    firstName: blocks.observable('John')
  });
</script>
<div data-query="setClass(firstName())">
  My name is {{firstName()}}!
</div>
```

## Events

All observables have some common events you could subscribe to:

* changing - fires before an observable value is changed. Could be canceled by returning false

```javascript
var number = blocks.observable(4).on('changing', function (newValue, oldValue) {
  // newValue - is the value that will be assigned to the observable
  // oldValue - is the current value of the observable before it will be changed

  if (newValue < 0) {
    // return false will prevent the value from changing
    return false;  
  }
});

// in the current scenario the value will not be changed because it is a negative integer
number(-1);
// alerts 4
alert(number());

// now the value will be changed successfully
number(2);
// alerts 2
alert(number());
```

* change - fires after an observable value have been changed

```javascript
var number = blocks.observable(4).on('change', function (newValue, oldValue) {
  // newValue - is the newly changed value
  // oldValue - is the previous value

  alert(newValue);
  alert(oldValue);
});

// this will alert 3(the new value) and then 4(the old value)
number(3);
```
