# Filtering, Sorting and Paging

## Filtering

```html
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
<input data-query="val(filterValue)" />

<!-- Using the items.view property which contains the filtered items -->
<ul data-query="each(items.view)">
  <li>{{$this}}</li>
</ul>
```

[Read filtering extender API](../api.md#blocks-observable-extenders-filter)

## Sorting

```html
<script>
  function Model() {
    this.names = ['Nancy', 'Janet', 'Margaret', 'Anne', 'Steven', 'Michael', 'Laura'];
    this.items = blocks.observable(this.names).extend('sort');
  }

  blocks.query(new Model());
</script>

<h2>Not sorted data</h2>
<ul data-query="each(items)">
    <li>{{$this}}</li>
</ul>

<h2>Sorted data</h2>
<!-- Using the items.view property which contains the sorted items -->
<ul data-query="each(items.view)">
    <li>{{$this}}</li>
</ul>
```

[Read sorting extender API](../api.md#blocks-observable-extenders-sort)

## Paging

```html
<script>
  function Model() {
    this.data = blocks.range(1, 74);
    this.skip = blocks.observable(0);
    this.take = 10;
    this.pages = blocks.range(1, Math.ceil(this.data.length / this.take) + 1);
    this.items = blocks.observable(this.data)
                      .extend('skip', this.skip)
                      .extend('take', this.take);

    this.setPage = function (e) {
      this.skip((blocks.dataItem(e.target) - 1) * this.take);
    }
  }

  blocks.query(new Model());
</script>
<!-- Using the items.view property which contains the paged items -->
<ul data-query="each(items.view)">
    <li>{{$this}}</li>
</ul>
<div data-query="each(pages)">
    <a href="#" data-query="click($root.setPage)" style="margin-right: 5px;">{{$this}}</a>
</div>
```

[Read paging extender API](../api.md#blocks-observable-extenders-paging)