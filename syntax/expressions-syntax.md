# `{{expressions}}` syntax

Expressions are a easy way to display a value in the HTML without using a [`data-query`](../syntax/data-query-syntax.md).

```html
<script>
  blocks.query({
    userRole: 'admin',
    profile: {
      username: 'jdoe'
    },

    price: 2.01,
    ratio: 0.76
  });
</script>

<!-- expressions could also be found in attributes -->
<h3 class="user {{userRole}}">
  Welcome, {{profile.username}}.
<h3>

<!-- you could place logic in expressions -->
<input value="{{price * ratio}}" />
```