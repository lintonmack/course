:twisted_rightwards_arrows: **Driver and Navigator switch roles if you haven't already done so**

## Testing the controller for `post.register`

1. Inside `User.test.js`, add a new test `register static is called when we post to the register route`.

2. Inside the test callback, spy on the `register` static method on the `User` object, and assign the spy to a variable named `spy`.

3. Assign an empty object literal to a variable named `req`, and underneath assign another to a variable named `res`.

4. Again, we will use `body-parser` to parse our actual form, which will add the input field names and values onto properties on the `req.body` object. We therefore need to mock our `req` object to have these fields. 

Add a `body` property to your `req` object. Set its value to an empty object literal.

Inside the object literal, add a property of `emailAddress`, with a value of `hello@world.com`, a property of `password` with a value of `password123`, and a property of `confirmPassword` with the value of `password123`.

6. Call the `register` method on the `usersControllers` object. Pass in `req` and `res` as arguments.

7. Now expect your spy to have been called with `req.body`.

Done? Ask for a code review.

8. Run your tests. You should fail with:

```js
Expected spy to have been called with:
[{"confirmPassword": "password123", "emailAddress": "hello@world.com", "password": "password123"}]
But it was not called.
```

## Pass the test

Create a new controller method inside `usersControllers.js` called `register`. It should take parameters `req` and `res`. Inside the function block, call `register` on `User` and pass in `req.body`.

You should now pass.

## Add, commit and push

:twisted_rightwards_arrows: **Driver and Navigator switch roles**

[Continue to part 8](lesson1_part8.md)
