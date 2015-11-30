# Model - plug in a service

> Note: Only [Properties](../property/introduction.md) will get transferred to the server. Observables and other values will not. 

## Creating a record

```javascript
var Profile = App.Model({
  options: {
    idAttr: 'id',

    create: {
      url: 'profile/create'
    }
  }
});

var profile = Profile({
    username: 'user1'
});

profile.sync();
```

## Updating a record

```javascript
var Profile = App.Model({
  options: {
    idAttr: 'id',

    update: {
      url: 'person/update'
    }
  },

  changePassword: function (newPassword) {
    this.password(newPassword);
    this.sync();
  }
});
```

## Deleting a record

```javascript
var Person = App.Model({
  options: {
    idAttr: 'id',

    destroy: {
      url: 'person/destroy'
    }
  },

  deleteItem: function () {
    this.destroy();
    this.sync();
  }
});
```

> You could find how to populate collection of objects from a service [here](../collection/plug-in-a-service.md)
