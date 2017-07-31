:twisted_rightwards_arrows: **Driver and Navigator switch roles if you haven't already done so**

## Adding to-dos

We haven't specified an `action` attribute on our `form` tag, so by default it will post to itself (in this case `/`). That's absolutely fine, but we need to add a route handler for POST requests on `/`. In order to be able to access form data on the server, we also need to install [body-parser](https://github.com/expressjs/body-parser), which is [middleware](https://www.safaribooksonline.com/blog/2014/03/10/express-js-middleware-demystified/) for Express. 

1. Install `body-parser`, saving it to your dependencies:

```bash
npm install --save body-parser
```

2. At the top of `toDoController.js`, require in `body-parser`, assigning the exported object to a variable named `bodyParser`:

```js
var bodyParser = require('body-parser')
```

3. Before the `toDoController` function, add: 

```js
var urlencodedParser = bodyParser.urlencoded({ extended: false })
```

***
:bulb:

`urlencoded` means that we expect to receive request data from a form.
***

4. Now inside the `toDoController` function block, after the `app.get` route handler, create a new route handler for `app.post`. Pass in a first argument of `/`, a second argument of `urlencodedParser`, and a third argument of a callback function with `req` and `res` parameters:

```js
app.post('/', urlencodedParser, function (req, res) {

})
```

***
:bulb:

We have an extra parameter here before our callback. This is route-specific middleware (i.e an extra action that can take place on our `req` object before it's passed to us in the callback). In this scenario, our `urlencodedParser` refers to the `body-parser` middleware. It will assign the values of our form fields to `req.body` so we can access our task with `req.body.item` (because our text input has the name `item`).
***

5. We can now access our form input with `req.body.item` so lets use it to add a to-do. Inside the callback for our post handler, call `toDos.addItem(req.body.item)`:

```js
app.post('/', urlencodedParser, function (req, res) {
  toDos.addItem(req.body.item)
})
```

6. Now we just need to render the page again with the latest data:

```js
app.post('/', urlencodedParser, function (req, res) {
  toDos.addItem(req.body.item)

  res.render('home', {
    toDos: toDos.getItems()
  })
})
```

## Add, commit and push

:twisted_rightwards_arrows: **Driver and Navigator switch roles**

[Next](lesson1_page5.md)
