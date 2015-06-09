# Property validation

Property supports validation. Here is a quick example:

```javascript
var App = blocks.Application();

var User = App.Model({
  username: App.Property({
    required: 'username is required',

    validateOnChange: true
  }),

  email: App.Property({
    email: 'Please enter a valid email',
    minlength: {
      value: 3,
      message: 'The email should be bigger than 3 symbols'
    },

    maxErrors: 2,

    validateOnChange: true
  })
});

App.View('SignUp', {
  user: User()
});
```

```html
<div data-query="view(SignUp)">
    <div data-query="with(user)">
        <input data-query="val(email)" placeholder="try entering an invalid mail or value smaller than 3 symbols" style="width:100%">
        <span data-query="visible(!email.valid()).html(email.errorMessages)"></span>

        <br />
        <br />

        <input placeholder="try not entering a value here" data-query="val(username)" style="width:100%;">
        <!-- showing the validation error in a message -->
        <span data-query="visible(!username.valid()).html(username.errorMessage)"></span>
    </div>
    <div data-query="visible(!user.valid())">
        <h2>All validation errors:</h2>
        <ul data-query="each(user.validationErrors)">
            <li>{{$this}}</li>
        </ul>
    </div>
</div>
```

## Validation properties & methods

Each Property have three exposed observables for controlling the validation:
 * **validate()** - call this method to validate and update all values below
    ```javascript
    user.username.validate();
    ```
 * **valid()** - is the validators have successfully passed
    ```html
    <span data-query="visible(!username.valid())"></span>
    ```
 * **errorMessage()** - the error message for the failed validator. If the validation have succeeded the value is empty string.
    ```html
    <h2>{{username.errorMessage}}</h2>
    ```
 * **errorMessages()** - all error messages for all failed validators. If the validation have succeeded the array is empty.
    ```html
    <ul data-query="each(username.errorMessages)">
      <li>{{$this}}</li>
    </ul>
    ```
<br />

Additionally, each Model have two observables that collect data from each Property to provide validation data for the entire Model.
 * **validate()** - call this method to call all Model Property validate() methods and update all their values and the Model observables described below
    ```javascript
    user.validate();
    ```
 * **valid()** - are all validators for all properties in the model have succeeded
    ```html
    <h2 data-query="visible(!profile.valid())">
      There is at least one validation error in the Model.
    </h2>
    ```
 * **validationErrors()** - all error messages from all failed validators in the entire Model
    ```html
    <ul data-query="each(username.validationErrors)">
      <li>{{$this}}</li>
    </ul>
    ```

## Validators

Here is a code example that describes all available validators that are supported out of the box.

```javascript
var Article = App.Model({
  propertyForValidation: App.Property({
    required: 'This field is required',

    email: 'The field should be a valid email',

    url: 'The field should be a valid URL',

    date: 'The value should be a valid date',

    number: 'The value should be a number',

    digits: 'The value should contain only digits',

    letters: 'The value should contain only letters',

    creditcard: 'The value should be a valid credit card number',

    min: {
      value: 0,
      message: 'The value should be a positive number'
    },

    max: {
      value: 100,
      message: 'Your age should be less than 100 years'
    },

    minlength: {
      value: 6,
      message: 'Your password should be longer than 5 symbols'
    },

    maxlength: {
      value: 19,
      message: 'Your username should be shorter than 20 symbols'
    },

    regexp: {
      value: /[0-9]+ [0-9]+ [0-9]+/,
      message: 'Your telephone should be in three groups of digits separated by space'
    },

    equals: {
      value: '1739',
      message: 'Your hardcoded password does not match'
    },

    asyncValidate: {
      // the function accepts a ready callback which should be called when validation decision could be made
      value: function (ready) {
        // do any async work here
        // example: go to the server to check sign in data

        // pass false or true for validation failure or success
        ready(false);
      },
      message: 'Your username or password is incorrect'
    },

    validate: function (value) {
      var number = parseFloat(value);
      if (blocks.isNaN(number)) {
        return 'Value should be a valid number';
      }
      if (number % 2 == 0) {
        return [
          'Value should not be an even number',
          'Value should be an odd number'
        ];
      }
      return true;
    }
  })
});
```

## Additional validation options

Property have additional properties that control the validation behavior. Take a look at the code comments:

> Note: All properties are with their default values

```javascript
var Product = App.Model({

  phone: App.Property({
    // determines if the validation is fired on every value change or will be called only manually from the validate() method
    validateOnChange: false,

    // determines the max numbers of validation errors to be pushed to the property.errorMessages collection
    maxErrors: 1,

    // determines if the validation will be fired the first time a value is assigned to the property or will wait for validate() to be called
    validateInitially: false  
  })
});
```
