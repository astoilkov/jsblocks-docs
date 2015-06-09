# `data-query` syntax

jsblocks aims to reduce learning process by making data-query syntax as familiar to technical people as possible. Calling a query is like calling a method which returns a query so chaining is possible.

```html
<ul data-query="each(items).setClass(listClassName)">
  <li data-query="html(title)"></li>
</ul>
```

> Note: if and ifnot queries expect queries as second and third parameters

```html
<h1 data-query="if(false, html(title), html('no title available'))"></h1>
<h1 data-query="ifnot(true, html('no title available'))"></h1>
```

> Note: Event queries expect callback functions as a parameter

```html
<div data-query="click(handler).on('touchend', handler)">
</div>
```
