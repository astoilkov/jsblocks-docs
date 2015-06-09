# Extending observable functionality

[`blocks.observable.extend()`](../api.md#blocks-observable-extend) method could be used to extend a particular observable functionality.
Great example is value formatting. Let's build value formatter which could be used for a lot of cases.

Before using `extend()` you will need to implement the formatting logic. After that the formatter could be used for any observable:

```javascript
// Creating an extender. It should be added as a property on the blocks.observable object
blocks.observable.formatter = function (formatCallback) {
    // The idea behind the formatter is to create an additional property called displayValue
    // which could be used in data-queries to show the formatter value and in the same time
    // use the original observable to work with the raw integer value
    // <span>{{goldPrice.displayValue}}</span>

    // creating a displayValue property on the observable because this points to the observable
    // creating a dependency observable so we could control value assignments
    this.displayValue = blocks.observable({

        // sets the value by calling the format callback and assigning its result
        set: function (value) {
            // this points to the displayValue observable
            this._value = formatCallback(value);
            alert('formatted');
        },

        // returns the value
        get: function () {
            // this points to the displayValue observable
            return this._value;
        }
    });

    this.on('change', function () {
        this.displayValue(this());
    });

    this.displayValue(this());

    // it is possible to return an observable here which will return the observable when calling this extender
    // this is not necessary here because by default if you do not return observable the extender will return itself
    // so writing return this; will have the same effect as leaving it without the return
};

// initializing a formatter, providing the format callback parameter
// the code alerts formatted because the value is formatted initially
// Note: every parameter after the first is passed to the extender function
var goldPrice = blocks.observable(3).extend('formatter', function (value) {
    // a simple example that parses the value and appends to zeros to the end
    return parseInt(value, 10) + '.00';
});

// alerts 3
alert(goldPrice());

// alerts 3.00
alert(goldPrice.displayValue());

// alerts formatted
goldPrice(41);

// alerts 41
alert(goldPrice());

// alerts 41.00
alert(goldPrice.displayValue());
```
