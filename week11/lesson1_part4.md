:twisted_rightwards_arrows: **Driver and Navigator switch roles if you haven't already done so**

## The GET `/login` route

1. Create a new file in `views/` called `login.hbs` and add the following:

```html
<form method="post">
  <input type="email" name="emailAddress">
  <input type="password" name="password">
  <button type="submit">Log In</button>
</form>
```

2. Inside `usersRoutes.js`, add a new GET route handler for `/login` and inside the callback, render the `login` template.

## The POST '/login` route

1. Create a new POST route handler for `/login` in `userRoutes.js`. Pass `urlencodedParser` as the second argument, `usersControllers.login` as the third argument and an anonymous function with `req` and `res` parameters as a fourth argument:

```js
app.post('/login', urlencodedParser, usersControllers.login, function (req, res) {

})
```

3. Finally, inside the anonymous function callback, redirect to the home page:

```js
res.redirect('/')
```

## Add, commit and push

:twisted_rightwards_arrows: **Driver and Navigator switch roles**

[Continue to part 5](lesson1_part5.md)