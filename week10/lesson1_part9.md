
## Login should store a session

Sessions allow us to keep a user authenticated on the server after page refreshes, and even after they shut down their computers. A session is stored on the server and in its most basic form will consist of the user's ID (from the database) and when their session expires (an amount we specify). When a session is created, a cookie is stored on the user's machine along with a secret key. On our apps, we can check this cookie against the server's stored sessions to see if the user is logged in - this stops us from having to show them the login page every time.

We'll use an npm package called `client-sessions` to store our sessions.

## Install `client-sessions`

```bash
npm install --save client-sessions
```

## Test - `usersControllers.login` creates a session

1. Add a new test to `User.test.js` called `login controller creates a session`.

2. Inside the callback, create `req` and `res` objects and add `req.body`, `req.body.emailAddress` and `req.body.password`, as you did in the previous test.

3. To store our sessions with `client-sessions`, we store our session data on `req.user`. We're going to store the user's email address. Add a `user` property to your `req` object, and assign to it an empty object literal.

4. Call `User.register` and pass in `req.body` as the first argument, and an anonymous function as the second argument (its callback function).

5. Inside the callback function, call `usersControllers.login` and pass `req`, `res` as the first two arguments and an anonymous function as a third argument.

6. Inside the `usersControllers.login` callback, expect `req.user.session` not to be undefined. Then call `done()`.

***
:bulb:

Here we expect our `req` object to have a `session` property. JavaScript objects pass by reference, meaning that if we pass them through to a method and that object modifies them, then whenever we access the object, we will receive the modified values.
***

7. Now run your tests. You should fail with `Expected value not to be undefined, instead received undefined`.

8. Our test is telling us that `req.user.session` is undefined.

## Making the test pass

Inside `usersController.js`, modify the `login` method to look as follows:

```js
  login: function (req, res, next) {
    User.login(req.body, function (error, result) {
      if (!error) {
        req.user.session = result
        next()
      }
    })
  },
```

To break this down, we've added a `next` parameter, which in Express is an action to take when the router handler has finished. We can use this `next` parameter to pass a callback in our test so we can call `done()` and make Jest wait. 

Inside our `User.login` callback, we are also setting `req.user.session` to the result of the query. When we eventually hook up our code to Express and we configure sessions, the resulting user will be stored as a session on the server.

Now run your tests. You should pass the test in question, but the modifications will have broken the test `login static is called when we post to the login route`. The reason is that we expect the spy in that test to be called with one argument, and it's now being called with two. You could fix this test by passing in a mock to the `usersController.login` as a third parameter, and by asserting it, but actually we can remove this test altogether. The reason being that we're testing the login static is called as part of our new test!