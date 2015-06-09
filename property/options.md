# Property options

Property have couple of advantages over an observable like [validation](validation.md), field mapping, support for default values and also are easier to setup.

```javascript
var App = blocks.Application();

var Article = App.Model({
  author: App.Property({

    field: 'Author',

    defaultValue: 'John Doe',

    // changing:
    // change:
    // add:
    // adding:
    // remove:
    // removing:
  }),

  date: App.Property({
    on: {
      changing: function () {

      }
    }
  }),

  info: App.Property({
    value: function() {
      return this.author() + ' ' + this.date();
    }
  })
});
```
