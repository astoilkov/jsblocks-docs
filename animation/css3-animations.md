# CSS3 Animations

CSS3 Animations are a perfect fit when you need more advanced control over your CSS animation.

Let's build the same example seen in [CSS3 Transitions](css3-transitions.md) but using CSS3 Animations so we could compare the differences.

```css
/* the show animation definition which goes from 0 to 1 opacity to achieve a fade in effect */
@keyframes show {
  from { opacity:0; }
  to { opacity:1; }
}

/* support for webkit browsers */
@-webkit-keyframes hide {
  from { opacity:1; }
  to { opacity:0; }
}

/* the hide animation definition which goes from 1 to 0 opacity to achieve a fade out effect */
@keyframes hide {
  from { opacity:1; }
  to { opacity:0; }
}

/* support for webkit browsers */
@-webkit-keyframes hide {
  from { opacity:1; }
  to { opacity:0; }
}

/* applying the show animation to the <li> item when being showed */
.item.b-show {
  -webkit-animation:0.5s show;
  animation:0.5s show;
}

/* applying the hide animation to the <li> item when being hidden */
.item.b-hide {
  -webkit-animation:0.5s hide;
  animation:0.5s hide;
}
```

```html
<input data-query="val(filterValue)" />

<!-- Using the items.view property which contains the filtered items -->
<ul data-query="each(items.view)">
    <li class="item">{{$this}}</li>
</ul>

<script>
  function Model() {
    this.filterValue = blocks.observable();
    this.names = ['Anne', 'Nancy', 'Janet', 'Margaret', 'Steven', 'Michael', 'Laura'];

    // creating the items and using the filter extender
    // this creates a view property which contains the filtered result
    this.items = blocks.observable(this.names).extend('filter', this.filterValue);
  }

  blocks.query(new Model());
</script>
```