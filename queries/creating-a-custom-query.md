# Creating a custom query

In some cases you will need to create your own data-query method so you could reuse code logic. Let's build a simple example.

```javascript
blocks.queries.formatPrice = {

  // the value is passed when calling the formatPrice
  update: function (value) {
    // this points to the HTML element
    if (value != null) {
      this.innerHTML = 'formated value: ' + value.toString();
    } else {
      this.innerHTML = '';
    }
  }  
};
```

And this is how you could use your query:

```html
<span data-query="formatPrice(price)"></span>
```

## Building custom queries with performance in mind

```javascript
blocks.queries.formatPrice = {

  preprocess: function (value) {
    // this points to the blocks.VirtualElement instance

    if (value != null) {
      this.html('formated value: ' + value.toString());
    } else {
      this.html('');
    }
  },

  // the value is passed when calling the formatPrice
  update: function (value) {
    // this points to the HTML element

    if (value != null) {
      this.innerHTML = 'formated value: ' + value.toString();
    } else {
      this.innerHTML = '';
    }
  }  
};
```
