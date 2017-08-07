:twisted_rightwards_arrows: **Driver and Navigator switch roles if you haven't already done so**

## Testing an Express route for login

We need to test the callbacks we will pass to Express route handlers (i.e. `app.get` and `app.post`) to ensure that they make calls to our models. These callbacks are essentially our controllers. We need to abstract them away from the route handlers though, so we can access them inside of our tests.

1. Inside `User.test.js`, add a new test `login static is called when we post to the login route`.

2. Inside the test callback, spy on the `login` static method on the `User` object, and assign the spy to a variable named `spy`.

3. Now we want to fake the `req` and `res` data that Express normally passes to our callback functions, as we want to test them without Express. Assign an empty object literal to a variable named `req`, and underneath assign another to a variable named `res`.

4. When we create our actual HTML login form in a Handlebars template, we will use `body-parser`, which will add the input field names as properties on `req.body` (e.g. `req.body.emailAddress`) and the values will be the values of the inputs. Therefore we need to mock our `req` object to have these fields. 

Add a `body` property to your `req` object. Set its value to an empty object literal.

Inside the object literal, add a property of `emailAddress`, with a value of `hello@world.com`, and a property of `password` with a value of `password123`.

5. We're going to abstract our callback functions into an object exported from a file stored inside of a `routes` folder (don't make it yet). For now, assume it exists. At the top of `User.test.js`, require in `../routes/usersRoutes.js`, and assign the exported object to a variable named `usersRoutes`.

6. Back inside your `test` callback, call the `login` method on the `usersRoutes` object. Pass in `req` and `res` as arguments.

7. Now expect your spy to have been called with `req.body.emailAddress` and `req.body.password`.

Done? Ask for a code review.

8. Run your tests. You should fail with `TypeError: usersRoutes.login is not a function`.

[Continue to part 5](lesson1_part5.md)
