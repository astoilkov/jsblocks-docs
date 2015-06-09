# Filtering, sorting & paging a Collection

MVC Collection is an observable so adding filtering, sorting or paging could be done the same way you would do it for an observable.

> Note: Filter, sorting and paging extenders create additional 'view' property observable which you could use to display the manipulated data

## Filtering

```html
<script>
  var App = blocks.Application();

  var Products = App.Collection({

  });

  var productsData = [{
    name: 'bread'
  }, {
    name: 'sweets'
  }, {
    name: 'soups'
  }];

  App.View('Details', {
    filterValue: blocks.observable(),

    products: Products(productsData).extend('filter', function (value) {
      var filter = this.filterValue();
      return !filter || value.name().indexOf(filter.toLowerCase()) != -1;
    })
  });
</script>
<div data-query="view(Details)">
    <input data-query="val(filterValue)" />

    <!-- Using the items.view property which contains the filtered items -->
    <ul data-query="each(products.view)">
        <li>{{name}}</li>
    </ul>
</div>
```
