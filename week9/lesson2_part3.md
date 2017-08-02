:twisted_rightwards_arrows: **Driver and Navigator switch roles if you haven't already done so**

## Retrieving ToDo Items

Inside `toDoController.js`, find the `app.get` `/` route handler. At the top of the callback function block add:

```js
ToDo.find({}, function (error, results) {

})
```

`ToDo` references our model, which is synced to a collection inside our database. We can do `.find({})` on that model to get back all of the documents in the ToDos collection (`{}` here means *all*. We can pass in field names and values to find specific records, which we'll be doing shortly for deleting items). 

Then move the below code into the callback:

```js
ToDo.find({}, function (error, results) {
  res.render('home', {
    toDos: toDos.getItems()
  })
})
```

We have to put our render in a callback, because if we don't then the template will be rendered before the data is ready (database requests are asyncronous).

Change `toDos.getItems()` to `results`:

```js
ToDo.find({}, function (error, results) {
  res.render('home', {
    toDos: results
  })
})
```

We should throw an error if there is one:

```js
ToDo.find({}, function (error, results) {
  if (error) {
    throw new Error(error)
  }

  res.render('home', {
    toDos: results
  })
})
```

Lastly, in `home.hbs` change `{{id}}` to `{{_id}}` - Mongo automatically creates unique identifier fields on each document using `_id`:

```html
    {{#each toDos}}
      <li data-id="{{_id}}">{{task}}</li>
    {{/each}}
```

:twisted_rightwards_arrows: **Driver and Navigator switch roles**

[Continue to part 4](lesson2_part4.md)