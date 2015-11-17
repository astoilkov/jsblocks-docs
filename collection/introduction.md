# Collections

Collections are a way to represent repeating data and allow CRUD operations from a remote service. Collections internally are of type [`blocks.observable`](../working-with-observables/introduction.md) and hold items of type [`Model`](../model/introduction.md).

```javascript
var App = blocks.Application();

var Users = App.Collection({
  // called when the collection is created
  init: function () {
    // to any initialization work here
  },

  // dependency observable that keeps track of the collection length
  count: blocks.observable(function () {
    return this().length;
  })
});

App.View('Profiles', {
  users: Users([{ username: 'admin' }]),

  username: blocks.observable(),

  addNewUser: function () {
    this.users.push({
      username: this.username()
    });
    this.username('');
  }
});
```

```html
<div data-query="view(Profiles)">
  Username: <input data-query="val(username)" />
  <button data-query="click(addNewUser)">Add new user</button>
  <ul data-query="each(users)">
    <li>{{username}}</li>
  </ul>
  <h3>Total count {{users.count}}</h3>
</div>
```

> Note: When choosing between using pure observables and Collection consider that pure observables have performance benefits over Collection. However, Collection provide you with a lot of flexibility and is best for your architecture. In general choose pure observables only when performance is a must.