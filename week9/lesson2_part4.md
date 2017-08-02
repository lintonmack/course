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

Now give your application a go. Everything should be working. If you click on the `Collections` tab in mLab you can even see your data as it appears in the database!

:tada: