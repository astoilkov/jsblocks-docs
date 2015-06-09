# Event queries

The events below are available out of the box as direct queries. In all other cases you could use the `on()` data-query to subscribe to an event.

```javascript
// mouse events
'click dblclick mousedown mouseup mouseover mousemove mouseout';

// keyboard events
'keydown keypress keyup';

// form events
'select, change, submit, reset, focus, blur';
```

And here is an example of using the click event:

```html
<script>
blocks.query({
  // the event passed to the handler is normalized like a jQuery event
  // e.target, e.relatedTarget, e.pageX, e.pageY, e.which, e.metaKey are normalized
  clicked: function (e) {
    // this points to the model
    this.clickCount(this.clickCount() + 1);
  },

  clickCount: blocks.observable(0)
});
</script>

<button data-query="click(clicked)">Click me</button>

<span>The button have been clicked {{clickCount}} times.</span>
```

## The `on()` data-query

Use the `on()` query when you need an event that is not available out of the box.

```
<a data-query="on('touchend', mobileClick)"></a>
```