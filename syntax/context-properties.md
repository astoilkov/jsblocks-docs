# Context properties

In order to understand the idea behind context properties take a look at this example:

```html
<div data-query="each(items)">
  <!-- $index is equal to the index for the current iteration -->
  <span>Item number {{$index}}</span>
</div>
```

> Note: All context properties are prefixed with $

But what exactly is a context and when it changes. In the above example
the context outside and inside the `<ul>` element is different. The context
have changed after calling `each()` method.

Let's look at a simple example by using the `$this` context property which points
to the current model object you are in:

```html
<script>
blocks.query({
  // the items that will be iterated
  items: ['first', 'second']
});
</script>
<!-- $this here points to the object passed to the blocks.query() function -->
<span>{{$this}}</span>

<!-- the context inside of the <ul> will be different because of the each() -->
<ul data-query="each(items)">
  <!-- $this here points to the current item that is being iterated from the collection -->
  <li>{{$this}}</li>
</ul>
```

The above example will produce the following HTML:

```html
<script>
blocks.query({
  items: ['first', 'second']
});
</script>
<!-- $this here points to the object passed to the blocks.query() function -->
<!-- its toString() method is called which results in [object Object] -->
<span>[object Object]</span>
<ul data-query="each(items)">
  <!-- in the first iteration $this points to the first item in the array which is 'first' -->
  <li>first</li>
  <!-- in the second iteration $this points to the second item in the array which is 'second' -->
  <li>second</li>
</ul>
```

## Available properties

### `$this`

#### Type - `*`
#### Description - points to the value for the current context you are in

---

### `$index`
#### Type - `blocks.observable`
#### Description - points to the index for the current each() iteration
> Note: only available in `each()` queries, otherwise `null`

---

### `$root`
#### Type - `*`
#### Description - points to the object passed to the
> Note: `$root = $this` until context is changed

---

### `$parent`
#### Type - `*`
#### Description - points to the parent context value
> Note: `null` until context is changed

---

### `$parents`
#### Type - `Array`
#### Description - array of all parent context values
> Note: `$parents.length = 0` until context is changed

---

### `parentContext`
#### Type - `Context`
#### Description - points to the parent context object which contains all properties defined in the table
> Note: `null` until context is changed

---

### `$view`
#### Type - `View`
#### Description - points to the current view you are in
> Note: `null` until view() data-query is called