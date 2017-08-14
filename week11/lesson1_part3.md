:twisted_rightwards_arrows: **Driver and Navigator switch roles if you haven't already done so**

## The GET `/register` route

1. Create a new file in `views/` called `register.hbs` and add the following:

```html
<form method="post">
  <input type="email" name="emailAddress" placeholder="Email Address">
  <input type="password" name="password" placeholder="Password">
  <button type="submit">Register</button>
</form>
```

2. Inside `usersRoutes.js`, add a new GET route handler for `/register` and inside the callback, render the `register` template.

## The POST '/register` route

1. Still inside `usersRoutes.js`, require in `usersControllers.js` and assign the exported object to `usersControllers`.

2. Create a new POST route handler for `/register` in `userRoutes.js`. Pass `urlencodedParser` as the second argument, `usersControllers.register` as the third argument and an anonymous function with `req` and `res` parameters as a fourth argument:

```js
app.post('/register', urlencodedParser, usersControllers.register, function (req, res) {

})
```

3. Finally, inside the anonymous function callback, redirect to the home page:

```js
res.redirect('/')
```

## Add, commit and push

:twisted_rightwards_arrows: **Driver and Navigator switch roles**

[Continue to part 4](lesson1_part4.md)