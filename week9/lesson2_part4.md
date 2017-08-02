:twisted_rightwards_arrows: **Driver and Navigator switch roles if you haven't already done so**

## Inserting ToDo items

Inside `toDosController.js`, take the code from the `app.get` callback and cut it into a function named `renderToDos` above the `todoController` function declaration:

```js
function renderToDos (res) {
  ToDo.find({}, function (error, results) {
    if (error) {
      throw new Error(error)
    }

    res.render('home', {
      toDos: results
    })
  })
}
```

Now add `renderToDos(res)` to the `app.get` callback:

```js
app.get('/', function (req, res) {
  renderToDos(res)
})
```

Because we render to-dos to the page on all 3 of our route handlers, we don't want to have to repeat the same code over and over again. If we needed to change it in one place then we'd have to change it in 2 other places. By encapsulating repetitive code into a function, we make it reusable and we keep our code DRY (Don't Repeat Yourself). We pass our `res` object into the function so we still get access to the `render` method that Express gives us.

Find the `app.post` `/` route handler. Replace `toDos.addItem(req.body.item)` with:

```js
ToDo({
  task: req.body.item
}).save(function (error) {
  if (error) {
    throw new Error(error)
  }

  renderToDos(res)
})
```

The above `ToDo(...).save()` is how we save a new record to the database. We pass an object into `ToDo()` with the field names and values we wish to add, then we call `.save()` when we're ready to save the information to the database. Again, we pass a callback where we render our page. If we rendered our page outside of the callback, then the page would render before the document had chance to be added to the collection, and our new to-do item wouldn't show on the page.

## Deleting ToDo items

Replace the contents of the `app.delete` callback with: 

```js
ToDo.find({ _id: req.body.id }).remove(function (error) {
  if (error) {
    throw new Error(error)
  }

  renderToDos(res)
})
```

Here we pass in a field name of `_id` to our selector (`{}`) with a value of the `id` field we sent in our XMLHttpRequest. This ensures that only a specific record with a matching `_id` gets returned to us. When this record gets returned, we get back an object which has a `remove` method on. `.remove()` will delete the matching document from the collection. 

Again, we wait for the remove action to take place before rendering our page, so the item doesn't still show on the page in our response.

Now give your application a go. Everything should be working. If you click on the `Collections` tab in mLab you can even see your data as it appears in the database! You may also notice that the collection storing our documents is called `todos`. Mongoose pluralises and lowercases our model name into a collection name. It is good practice for collections to adopt a lowercase or lowerCamelCase naming convention.

:tada: