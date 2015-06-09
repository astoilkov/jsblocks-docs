## CSS3 Transitions

Using CSS3 Transitions in jsblocks is the perfect and recommended way for animating elements in your page:
* Easy to use
* Transitions are played only in browsers that support CSS3 Animations which speeds your animation in modern browsers and doesn't slow down old browsers

> Note: The b-show, b-show-end, b-hide, b-hide-end classes are predefined by the jsblocks framework

```css
/* set transition options for all <li> elements */
.item {
  -webkit-transition:0.5s linear all;
  -moz-transition:0.5s linear all;
  -o-transition:0.5s linear all;
  transition:0.5s linear all;
}

/*
* The combination of b-show(start state) and b-show-end(end state) classes with
* opacity starting from 0 and ending at 1 achieves a fade-in effect when filtering
*/

/* b-show class represents the starting state when a item is being showed */
.item.b-show {
  opacity: 0;
}

/* b-show-end class represents the ending state when a item is being showed */
.item.b-show-end {
  opacity: 1;
}

/*
 * The same as the example above but for hiding items:
 * The combination of b-hide(start state) and b-hide-end(end state) classes with
 * opacity starting from 1 and ending at 0 achieves a fade-out effect when filtering.
*/

/* b-hide class represents the starting state when a item is being hidden */
.item.b-hide {
  opacity: 1;
}

/* b-hide-end class represents the ending state when a item is being hidden */
.item.b-hide-end {
  opacity: 0;
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

### `.b-show`
#### Represents the start state of the animation when showing or adding an element on the page

---

### `.b-show-end`
#### Represents the end state of the animation when showing or adding an element on the page

---

### `.b-hide`
#### Represents the start state of the animation when hiding or removing an element from the page

---

### `.b-hide-end`
#### Represents the end state of the animation when hiding or removing an element from the page