:twisted_rightwards_arrows: **Driver and Navigator switch roles if you haven't already done so**

## Retrieving ToDo Items

Inside `toDosController.js`, find the `app.get` `/` route handler. At the top of the callback function block add:

```js
ToDo.find({}, function (error, results) {

})
```

Then move the below code into the callback:

```js
ToDo.find({}, function (error, results) {
  res.render('home', {
    toDos: toDos.getItems()
  })
})
```

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