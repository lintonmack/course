:twisted_rightwards_arrows: **Driver and Navigator switch roles if you haven't already done so**

## Testing for logout

```js
test('logout clears the session', function () {
  var req = {
    session: {
      user: {
        emailAddress: 'email@example.com',
        password: 'password123'
      }
    }
  }
  var res = {}
  var next = jest.fn()

  usersControllers.logout(req, res, next)
  expect(req.session.user).toBeFalsy()
})
```

Broken down:

1. We create a pretend request object, with a `user` object attached to `req.session` (we pretend we have a session).

2. We mock `res` and `next` objects that our controller expects. Our controller will actually call `next()` as a callback, as it will be used as middleware. Therefore we assign `next` a mock function (in previous walkthroughs we've passed `done` to our controllers - we don't need to here as our `logout` controller won't perform any asyncronous database operations).

3. We then call a `logout` method on `usersControllers`, passing in our `req`, `res` and `next`.

4. Then we expect `req.session.user` to be a falsy value (we expect it to have been set to nothing).

## The GET `/logout` route

When we go to `/logout`, we want our session to be cleared and then to be redirected back to the homepage, where we should see ourselves no longer logged in.

1. Inside `usersControllers.js` add a new controller with `req`, `res`, and `next` parameters. Inside, set `req.session.user` to `false`, and then call `next()`:

```js
logout: function (req, res, next) {
  req.session.user = false
  next()
}
```

2. Run your tests. They should hopefully now pass.

3. Now, inside `usersRoutes.js`, add a new GET route handler for `/logout`. Give it two arguments: `usersControllers.logout` and an anonymous function with `req` and `res` parameters:

2. Inside the last callback, set `req.session.user` to `false`.

3. Then call `res.redirect('/')`:

```js
app.get('/logout', usersControllers.logout, function (req, res) {
  res.redirect('/')
})
```

***
:bulb:

As you may have guessed `res.redirect(...)` will redirect the user to whichever route is specified. 
***

## Add, commit and push

:twisted_rightwards_arrows: **Driver and Navigator switch roles**

[Continue to part 6](lesson1_part6.md)