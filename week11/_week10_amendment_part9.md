## Week 10 Amendment - Part 9, Storing Sessions

```js
req.user.session
```

should have been

```js
req.session.user
```

### Correct test inside `User.test.js`

```js
test('login static creates a session', function (done) {
  var req = {
    body: {
      emailAddress: 'hello@world.com',
      password: 'password123'
    },
    session: {}
  }
  var res = {}

  User.register(req.body, function (error, result) {
    usersControllers.login(req, res, function () {
      expect(req.session.user).not.toBeUndefined()
      done()
    })
  })
})
```

### Correct controller code inside `usersControllers.js`

```js
login: function (req, res, next) {
  User.login(req.body, function (error, result) {
    if (!error) {
      req.session.user = result
      next()
    }
  })
},
```