# JavaScript Animations

Programmatic animations using JavaScript are useful when you need cross browser support or some advanced animation depending on values that change. You are free to use any framework you want when animating using JavaScript.

```html
<script src="http://cdn.jsdelivr.net/velocity/1.1.0/velocity.min.js"></script>
<script>
blocks.query({
  visible: blocks.observable(true),
  toggleVisibility: function () {
    // this points to the model object passed to blocks.query() method
    this.visible(!this.visible());
  },

  fade: function (element, ready) {
    Velocity(element, {
      // this points to the model object passed to blocks.query() method
      opacity: this.visible() ? 1 : 0
    }, {
      duration: 1000,
      queue: false,

      // setting the ready callback to the complete callback
      complete: ready
    });
  }
});
</script>
<button data-query="click(toggleVisibility)">Toggle visibility</button>
<div data-query="visible(visible).animate(fade)" style="background: red;width: 300px;height: 240px;">
</div>

```
