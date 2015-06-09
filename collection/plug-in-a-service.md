# Collection - plug in a service

## Populating the collection with data

```javascript
var Articles = App.Collection({
  options: {
    read: {
      url: 'http://your-api.com/articles'
    }
  }
});

var articles = Articles().read();
```

> Create/Update/Delete operations could be done through the Model. More information [here](../model/plug-in-a-service.md)