:twisted_rightwards_arrows: **Driver and Navigator switch roles if you haven't already done so**

## Checking the user can only login when registered

We've asserted that our `User.login` static method calls `User.findOne` but we've not actually asserted whether a record exists, which is an issue as with our current code we could just be letting anybody login with any details. 

1. Inside `User.test.js`, create a new test `can't login if not registered`. Pass the `done` parameter to the callback function, as we're going to be using asyncronous code inside this test.

2. In the test's callback function, add a variable `user` as before:

```js
var user = {
  emailAddress: 'hello@world.com',
  password: 'password123'
}
```

3. Now call `User.login` as follows:

```js
User.login(user, function (error, result) {
  expect(error).not.toBeTruthy()
  expect(result).not.toBeTruthy()
  done()
})
```

Here we expect there not to be an error, and also not to be a result (a.k.a there is no user registered). Because it's an asyncronous action, we call `done()` so the callback has chance to happen.

4. Run your tests. They should all pass with no extra changes to be made!

## User can log in if registered

Now we need to test the user can login if registered:

```js
test('can login if registered', function (done) {
  var user = {
    emailAddress: 'hello@world.com',
    password: 'password123'
  }

  User.register(user, function (error, result) {
    User.login(user, function (error, result) {
      expect(error).not.toBeTruthy()
      expect(result).toBeTruthy()
      done()
    })
  })
})
```

Here we run our `register` static method, and we call the `login` method in the callback. This is so `register` has chance to finish, before we try and login. We then expect there not to be any errors, and we expect to have a result.
