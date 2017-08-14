## Week 10 Amendment - Part 7, Register static method

The `register` static should call `next`.

### Correct test inside `User.test.js`

```js
test('register static is called when we post to the register route', function () {
  var spy = spyOn(User, 'register')

  var req = {
    body: {
      emailAddress: 'hello@world.com',
      password: 'password123',
      confirmPassword: 'password123'
    }
  }
  var res = {}
  var callback = jest.fn()

  usersControllers.register(req, res, callback)

  expect(spy).toHaveBeenCalledWith(req.body, callback)
})
```

### Correct controller code inside `usersControllers.js`

```js
register: function (req, res, next) {
  User.register(req.body, next)
}
```